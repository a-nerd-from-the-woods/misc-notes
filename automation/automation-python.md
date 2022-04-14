# Automation With Python

## Executing Shell Commands Via Python

### Deprecated Methods

1. `os.system('YOUR-COMMAND-HERE')`
    * This method will run the command (entered as a string) in a subshell. If ran on a *NIX system, the command status code will be returned, on Windows based systems, however the output of the command ran will be return.
2. `os.popen('YOUR-COMMAND-HERE')`
    * This method of running commands will return an open file object connected to the pipe, which can be read or written too. The output of the command read can be returned via `os.popen('YOUR-COMMAND-HERE').read()`
3. `os.spawn(os.DESIRED_MODE_HERE, SHELL_PATH_HERE, COMMAND_TO_BE_RAN_HERE)`
    * Exucutes the commands passed to it in a new process. It has two methods, `P_NOWAIT`, which will make the function return the process id of the new process, or `P_WAIT`, which will return the process' exit code if the command is successfully ran, or `signal`, where signal is the signal that killed the process.

### Current Standard Methods

#### The `subprocess` Module

##### Current API
1. `run(YOUR_COMMAND)`
    * Runs the command, waits for completion returns a `CompletedProcess` instance.
2. `Popen(YOUR_COMMAND)`
    * A flexible class for executing a command in a new process.
##### Older API (x < Python 3.5)
1. `call(YOUR_COMMAND)`
    * Runs a command and then returns the status code.
2. `check_call(YOUR_COMMAND)`
    * Runs a command and then raises `CalledProcessError()` if return code is not `0`.
3. `check_output(YOUR_COMMAND)`
    * Similar to `check_call(YOUR_COMMAND)` but returns returns the contents of stdout (vs. the return code).
4. `getoutput(YOUR_COMMAND)`
    * Runs a command in a shell, waits for completion, returns output.
5. `getstatusoutput(YOUR_COMMAND)`
    * Runs a command in the shell, waits for completion, returns a tuple in (exitcode, command-output) format.


