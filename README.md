# freeCodeCamp - Build a Salon Appointment Scheduler

This is a solution to the freeCodeCamp project [Build a Salon Appointment Scheduler](https://www.freecodecamp.org/learn/relational-database/build-a-salon-appointment-scheduler-project/build-a-salon-appointment-scheduler).

## What I learned

### Learn Advanced Bash by Building a Kitty Ipsum Translator

- to redirect the command output you just did in terminal, ```<command> > <filename>```, this will automatically create the file
- ```<command> > <filename>``` creates or rewrites the file while ```<command> >> <filename>``` append command to the file
- ```> <filename>``` can empty file
- There’s two types of output, ```stdout``` (standard out) for when a command is successful, and ```stderr``` (standard error) for when it’s not. Both of these will print to the terminal by default. ```bad_command``` was not a valid command, so it printed to ```stderr```. 
- use ```1>``` to redirect stdout and ```2>``` to redirect stderr
- ```stdin``` (standard in) is the third thing commands can use and is for getting input. The default is the keyboard.
- Just like you can redirect output, you can redirect stdin as well. Here's an example: ```<command> < <filename_for_stdin>```
- ```<``` is the input redirection, it is used to take input from a file and feed it as input to a command: ```<command> < <filename>```
- Another way to set the stdin is by using the pipe (|). It will use the output from one command as input for another. Here's an example: ```<command_1> | <command_2>```. This will take the stdout from command_1 and use it as the stdin for command_2. For example, ```echo <your_name> | read NAME```; ```echo <your_name> | ./script.sh```; When you used the pipe (|) to set the input for read, it ran the command in a subshell or subprocess. Basically, another terminal instance within the one you see. The variable was set in there and didn't affect the one you had previously set. 
- ```cat``` is another command that takes input. it will print the contents of a file or input to stdout
- ```control+c``` will terminate command
- ```echo <your_name> | ./script.sh 2> stderr.txt```; this command not only provides your name as input, execute script.sh, but also redirects errors to stderr.txt. On top of that, You can redirect both the stderr and stdout by adding another redirection at the end like this: ```> <filename>```, if you add ```> stdout.txt``` at the end, you will find nothing will be printed in the terminal but all went to different files
- ```wc``` stands for word count. It showed you how many lines were in the file, how many words, and how many bytes: ```wc <filename>```
- to find manual of wc: ```man wc```
- ```wc -l``` will only print how many lines
- ```wc -w``` how many words
- ```wc -m``` how many characters
- Use ```cat``` to pipe the content of the file as the input of the wc command: ```cat <filename> | wc```; this will return almost the same outputs as ```wc <filename>``` except the filename. ```wc < <filename>``` will also only return numbers
- ```grep``` is a command for searching for patterns in text. You can use it like this: ```grep '<pattern>' <filename>```.
- to find manual of grep: ```man grep```
- ```grep --color``` will highlight the matching patterns
- ```grep -n``` can show line numbers, for example: ```grep --color -n ‘meow’ kitty_ipsum_1.txt```
- ```grep``` can use regular expressions, for example ```grep ‘meow[a-z]*’ kitty_ipsum_1.txt```
- ```grep -c``` counts the lines that having matching patterns
- ```grep -o``` will list all the matches in their own line
- with the help of ```wc -l```, you can count the number of all the matched patterns, for example: ```grep -o 'meow[a-z]*' kitty_ipsum_1.txt | wc``` 
- Check the results with grep for words that start with dog or woof. Here's an example of the search pattern you want: ```grep -E <dog_words>|<woof_words>```
- ```sed``` can replace text like this: ```sed 's/<pattern_to_replace>/<text_to_replace_it_with>/' <filename>```. By default, it won't replace the text in the file. It will output it to stdout. You can add regex flags after the last ```/``` in the sed argument. A ```g```, for global, would replace all instances of a matched pattern, without ```g```, ```i``` will only match one in one line, or an i to ignore the case of the pattern. Can also use ```sed 's/<pattern_to_replace>/<text_to_replace_it_with>/' < <filename>``` or ```cat <filename> | sed 's/<pattern_to_replace>/<text_to_replace_it_with>/'```
- to find manual of sed: ```man sed```
- ```sed -E``` enables the use of extended regular expressions.
- You can replace many patterns using sed like this: ```sed 's/<pattern_1>/<replacement_1>/; s/<pattern_2>/<replacement_2>/'```. Note that you need the semi-colon between the two replacement patterns and they both need to be wrapped in the quotes. 
- ```grep -n 'meow[a-z]*' kitty_ipsum_1.txt | sed -E 's/([0-9]+).*/\1/'``` this will only print the line numbers
- You can access an argument with ```$<argument_number>```, to access the first argument, ```$1```
- to run a script with argument: ```./script.sh <argument>```, you can use a file as argument
- ```diff``` is a command to view the difference between two files. You can use it like this: ```diff <file_1> <file_2>```.
- man diff
- ```diff --color <file_1> <file_2>```

### Learn Bash and SQL by Building a Bike Rental Shop

- In PostgreSQL, DEFAULT is a keyword used in SQL statements to specify a default value for a column when a new row is inserted into a table and no explicit value is provided for that column. When defining a table, you can specify a default value for a column using the DEFAULT keyword in the column definition. For example:
	```
	CREATE TABLE example_table (
    		id SERIAL PRIMARY KEY,
    		name VARCHAR(50) DEFAULT 'John',
    		age INT DEFAULT 30
	);
	```
- to set column unique when creating it, for example, ```ALTER TABLE customers ADD COLUMN phone VARCHAR(15) NOT NULL UNIQUE;```
- type date and default now() for example, ```ALTER TABLE rentals ADD COLUMN date_rented DATE NOT NULL DEFAULT NOW();```
- case statement:
	```
	case EXPRESSION in
 	 	PATTERN) STATEMENTS ;;
 	 	PATTERN) STATEMENTS ;;
 		 PATTERN) STATEMENTS ;;
  		*) STATEMENTS ;;
	esac
	```
	for example:
	```
	case $MAIN_MENU_SELECTION in
  		1) RENT_MENU ;;
  		2) RETURN_MENU ;;
  		3) EXIT ;;
  		*) MAIN_MENU ;;
	esac
	```
- if an argument exists, print it: 
    ```  
    if [[ $1 ]]
    then
        echo -e "\n$1"
    fi
  ```
- ```[[ 11 =~ ^[0-9]+$ ]]; echo $?``` returns 0, to check if it is not a number ```[[ ! 11 =~ ^[0-9]+$ ]]; echo $?```
- What you put the in subshell ```($(...))``` will be executed, and the result of it will replace the subshell. 