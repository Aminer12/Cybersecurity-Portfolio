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