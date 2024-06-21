# Advanced Bash Scripting

IBM Introduction to linux commnads and shell scripting

## Overview:

Shell Scripting

## Objectives

After completing this task, you will be able to:

1. Run sets of commands using conditional statements
2. Create true/false comparisons with logical operators
3. Use arithmetic operators to perform basic mathematical calculations
4. Use list-like arrays to store and access data
5. Execute repetitive tasks with for loops

### Skills

Linux commands, Shell scripting

#### Exercise 1 - Using conditional statements and logical operators

In this exercise, you will create a simple Bash script containing a conditional statement to handle the following tasks:

- Prompt the user for a Yes or No response to a question
- Print a response based on the user's answer

1. Create a new Bash script
   Create a Bash script file and make it executable.

2. Query the user and store their response
   Now get your script to:

Ask the user a binary "yes or no" question of your choosing
Store the user's answer in a variable.

3. Use a conditional block to select a response for the user
   Finally, use a conditional block to print a message to the user based on their response to your query.

#### Solution

1.           echo '#!/bin/bash' > conditional_script.sh
        chmod u+x conditional_script.sh

2.           #!/bin/bash

        echo 'Are you enjoying this course so far?'
        echo -n "Enter \"y\" for yes, \"n\" for no."
        read response

3.           #!/bin/bash

        echo 'Are you enjoying this course so far?'
        echo -n "Enter \"y\" for yes, \"n\" for no"
        read response
        if [ "$response" == "y" ]
        then
        echo "I'm pleased to hear you are enjoying the course!"
        echo "Your feedback regarding what you have been enjoying would be most welcome!"
        elif [ "$response" = "n" ]
        then
        echo "I'm sorry to hear you are not enjoying the course."
        echo "Your feedback regarding what we can do to improve the learning experience"
        echo "for this course would be greatly appreciated!"
        else
        echo "Your response must be either 'y' or 'n'."
        echo "Please re-run the script to try again."
        fi

#### Exercise 2 - Performing basic mathematical calculations and numerical logical comparisons

In this exercise, you will create a Bash script that performs basic arithmetic calculations on two integers entered by the user.
You will also use logical comparisons to determine which calculation leads to the greatest result.

1. Create a Bash script
   Create an executable Bash script that prompts the user for two integers, then stores and prints both the sum and product of the two integers.

2. Add logic to your script
   Add logic to your script that determines whether the sum is greater than, less than, or equal to the product. Display an appropriate statement corresponding to each possible result.

Assume the user inputs two integers. Don't worry about handling the case where the user inputs a non-integer string by mistake.

#### Solution

1.           #!/bin/bash

        echo -n "Enter an integer: "
        read n1
        echo -n "Enter another integer: "
        read n2

        sum=$(($n1+$n2))
        product=$(($n1*$n2))

        echo "The sum of $n1 and $n2 is $sum"
        echo "The product of $n1 and $n2 is $product."

2.           #!/bin/bash

        echo -n "Enter an integer: "
        read n1
        echo -n "Enter another integer: "
        read n2

        sum=$(($n1+$n2))
        product=$(($n1*$n2))

        echo "The sum of $n1 and $n2 is $sum"
        echo "The product of $n1 and $n2 is $product."

        if [ $sum -lt $product ]
        then
        echo "The sum is less than the product."
        elif [[ $sum == $product ]]
        then
        echo "The sum is equal to the product."
        elif [ $sum -gt $product ]
        then
        echo "The sum is greater than the product."
        fi

#### Exercise 3 - Using arrays for storing and accessing data within for loops

In this exercise, you will create a report based on a supplied dataset using the CSV format. You will extract the columns of the dataset into separate arrays and create a new column using arithmetic and array logic. Finally, you will combine the dataset with the new column and save the resulting report as a CSV file.

1. Download a CSV file to your current working directory
   The file, arrays_table.csv, is located at the following url:
   https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-LX0117EN-SkillsNetwork/labs/M3/L2/arrays_table.csv

2. Display the CSV file to understand what it looks like

3. Create a Bash script that parses table columns into 3 arrays

4. Create a new array as the difference of the third and second columns.

5. Create a report by combining your new column with the source table

#### Solution

1.          csv_file="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-LX0117EN-SkillsNetwork/labs/M3/L2/arrays_table.csv"
        wget $csv_file

2.          cat arrays_table.csv

3.          #!/bin/bash

        csv_file="./arrays_table.csv"

        # parse table columns into 3 arrays
        column_0=($(cut -d "," -f 1 $csv_file))
        column_1=($(cut -d "," -f 2 $csv_file))
        column_2=($(cut -d "," -f 3 $csv_file))

        # print first array
        echo "Displaying the first column:"
        echo "${column_0[@]}"

#### How to use:

Execute the following on your terminal

1.           ./conditional_script.sh
2.           ./prompt_script.sh

3.           ./column_table.sh

#### Others:

Incase you are using Windows/ Git Bash, instead of wget use curl like this:
curl -O https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-LX0117EN-SkillsNetwork/labs/M3/L2/arrays_table.csv
