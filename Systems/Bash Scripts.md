.sh -> extension used for shell scripts | but not mandatory 

inside the shell file
```
1 || #!/bin/bash
2 || echo "Hello, World!"

first line is a shebang, telling the system what interpreter to use
```
Remember to run the script we have to add execution privileges to the file using chmod 

running script
```
./hello.sh -> output the echo script

./ -> tell the system to look for the script in the current directory 
```

Creating Variables 
```
#!/bin/bash
PRICE_PER_APPLE=5 
MyFirstLetters=ABC 
greeting='Hello world!' 

# Escaping special characters 
echo "The price of an Apple today is: \$HK $PRICE_PER_APPLE" -> \$ is an escape so the symbol can be used naturally

# Avoiding ambiguity 
echo "The first 10 letters in the alphabet are: ${MyFirstLetters}DEFGHIJ" 

# Preserving whitespace 
echo $greeting -> Hello World!
echo "$greeting" -> Hello    World!
```

command substitutes are done using $() or backticks(\`\`) || which allow you to use the output of a command as the value of a variable 
```
# Command substitution 
CURRENT_DATE=$(date +"%Y-%m-%d") 
echo "Today's date is: $CURRENT_DATE" 

FILES_IN_DIR=$(ls) 
echo "Files in the current directory:" 
echo "$FILES_IN_DIR" 

UPTIME=$(uptime -p) 
echo "System uptime: $UPTIME"
```

Shell variables can also be used in arithmetic operations, using the $((expression))
```
#!/bin/bash 

X=10 
Y=5 

# Addition 
SUM=$((X + Y)) 
echo "Sum of $X and $Y is: $SUM" 

# Subtraction 

DIFF=$((X - Y)) 
echo "Difference between $X and $Y is: $DIFF" 

# Multiplication 
PRODUCT=$((X * Y)) 
echo "Product of $X and $Y is: $PRODUCT" 

# Division 
QUOTIENT=$((X / Y)) 
echo "Quotient of $X divided by $Y is: $QUOTIENT"

# Modulus (remainder) 
REMAINDER=$((X % Y)) 
echo "Remainder of $X divided by $Y is: $REMAINDER" 

# Increment X=$((X + 1)) 
echo "After incrementing, X is now: $X" 

# Decrement Y=$((Y - 1)) 
echo "After decrementing, Y is now: $Y"
```

Environmental Variables 
```
#!/bin/bash 

# Displaying some common environment variables 

echo "Home directory: $HOME" 
echo "Current user: $LOGNAME"
echo "Shell being used: $SHELL" 
echo "Current PATH: $PATH" 

# Creating a new environment variable export 
MY_VARIABLE="Hello from my variable"

# Displaying the new variable
echo "My new variable: $MY_VARIABLE" 
 
# Creating a child process to demonstrate variable scope bash -c 'echo "MY_VARIABLE in child process: $MY_VARIABLE"' # Removing the environment variable unset MY_VARIABLE # Verifying the variable is unset echo "MY_VARIABLE after unsetting: $MY_VARIABLE"
```
