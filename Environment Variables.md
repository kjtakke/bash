Environmental variables are dynamic values that affect the way processes and applications behave on a computer. They are part of the environment in which a process executes and provide a way to influence the operation of processes and are particularly useful in shell scripts. Here's a guide explaining their usage and management.

# Understanding Environmental Variables

## Commonly Used Environmental Variables

- **`PATH`**: Specifies a list of directories where executable programs are located. When you type a command, the shell looks through these directories to find the executable.

- **`HOME`**: Indicates the home directory of the current user.

- **`USER` or `USERNAME`**: Contains the name of the current user.

- **`SHELL`**: Represents the path of the current user's shell.

- **`LANG`**: Standard language settings for the system, which affects locale and encoding preferences.

- **`PWD`**: Stands for the present working directory, showing where the user is currently located in the directory tree.
  
- **`ENV` or `BASH_ENV`**: Points to a shell script that is executed whenever a new shell begins, setting up the environment.

## Managing Environmental Variables

### Viewing Environmental Variables

You can view the current environmental variables and their values using `env` or `printenv`:

```bash
printenv
```

```bash
env
```

To see the value of a specific variable:

```bash
echo $PATH
echo $HOME
```

### Setting Environmental Variables

#### Temporarily in a Shell Session

To set or change an environmental variable in a shell session temporarily (effective only in current session or script):

```bash
export VARIABLE_NAME="value"
```

Example:

```bash
export MY_VAR="Hello, World!"
echo $MY_VAR  # Outputs: Hello, World!
```

#### Permanently for a User

To set environmental variables permanently for a user, you should modify configuration files that are executed at login or when starting a shell:

1. **Bash Shell**:

   Edit `~/.bashrc` or `~/.bash_profile`:

   ```bash
   export VARIABLE_NAME="value"
   ```

   Apply changes with:

   ```bash
   source ~/.bashrc
   ```

2. **Zsh Shell**:

   Edit `~/.zshrc`:

   ```bash
   export VARIABLE_NAME="value"
   ```

   Apply changes with:

   ```bash
   source ~/.zshrc
   ```

### Permanently for All Users

To make environmental variables available to all users:

1. Edit `/etc/environment`: 

   This file is read by PAM to initialize the environment for whenever a user logs in. Lines should be of the form `VARIABLE=value`:

   ```plaintext
   VARIABLE_NAME="value"
   ```

2. Edit `/etc/profile` or add a script in `/etc/profile.d/`:

   These are executed for login shells.

   ```bash
   export VARIABLE_NAME="value"
   ```

### Unsetting Environmental Variables

To remove an environmental variable in the current session:

```bash
unset VARIABLE_NAME
```

### Exporting Variables

The `export` command makes a variable available to child processes started from the current shell session or script.

```bash
MY_VAR="data"
export MY_VAR
```

## Using Environmental Variables in Scripts

Environmental variables can be used to pass data between shell scripts and processes. Here's an example script:

```bash
#!/bin/bash

echo "The current user is: $USER"
echo "Home Directory is: $HOME"
echo "Executing in: $PWD"

# Use custom environmental variable
export API_KEY="Your-API-Key"
echo "The API Key is: $API_KEY"
```

## Conclusion

Environmental variables are a powerful tool for configuring and customizing the behavior of systems and applications. They facilitate communication within software systems by passing vital configuration data to multiple processes and scripts.

Key Points:
- Use environmental variables to store and pass configuration data.
- Manage these variables through shell-specific configuration files for persistent settings.
- Understand the scope of variables (session vs. persistent across reboots or login sessions).

Experiment and leverage environmental variables to streamline your shell scripts and system configurations for more efficient and manageable environments!