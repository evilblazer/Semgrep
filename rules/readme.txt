This folder contains modified/custom rules for semgrep and examples on why the default rules did not manage to find them. 


For example, I used the code injection examples from https://github.com/JoyChou93/java-sec-code/blob/master/src/main/java/org/joychou/controller/CommandInject.java and 
I referenced the default Java code injection yaml file from 
https://raw.githubusercontent.com/returntocorp/semgrep-rules/develop/java/lang/security/audit/command-injection-process-builder.yaml 

    public String codeInject(String filepath) throws IOException {

        String[] cmdList = new String[]{"sh", "-c", "ls -la " + filepath};
        ProcessBuilder builder = new ProcessBuilder(cmdList);
        builder.redirectErrorStream(true);
        Process process = builder.start();
        return WebUtils.convertStreamToString(process.getInputStream());
    }


Changes to default code injection yaml file,
1. I removed the extra pattern-not-inside as it is an incorrect assumption that a code injection cannot occur in the 2nd or last 
parameter of the parameter.


    - pattern-not-inside: |
        $CMD = Arrays.asList("...",...);
        ...
    - pattern-not-inside: |
        $CMD = new String[]{"...",...};
        ...
    - pattern-not: |
        $PB.command("...",...)
    - pattern-not: |
        $PB.command(new String[]{"...",...},...)
    - pattern-not: |
        $PB.command(Arrays.asList("...",...),...)
