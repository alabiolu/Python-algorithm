# Update a file through a Python algorithm

## Objective

I created an algorithm that removes IP addresses identified in a remove_list variable from the "allow_list.txt" file of approved IP addresses. This algorithm involved opening the file, converting it to a string to be read, and then converting this string to a list stored in the variable ip_addresses. I then iterated through the IP addresses in remove_list. With each iteration, I evaluated if the element was part of the ip_addresses list. If it was, I applied the .remove() method to it to remove the element from ip_addresses.. After this, I used the .join() method to convert the ip_addresses back into a string so that I could write over the contents of the "allow_list.txt" file with the revised list of IP addresses.


### Skills Learned


- Understanding core Python concepts like variables, data types, control flow (loops, conditionals), and functions.
- Proficiency in reading, writing, and appending to files using Python's built-in functions.
- Skills in processing and modifying file contents, such as parsing text, extracting information, and formatting output.
- Ability to design logical steps to achieve the desired file updates.
-  Identifying the core components of the file update task and creating a structured approach.
-  Considering potential issues and implementing error handling mechanisms.
-   Optimizing the algorithm for performance and resource usage.

### Tools Used

-  Python programming language.

## Steps
## Open the file that contains the allow list
For the first part of the algorithm, I opened the "allow_list.txt" file. First, I assigned this file name as a string to the import_file variable:

![Screenshot 2024-08-02 122025](https://github.com/user-attachments/assets/dc55c7d0-2993-4921-b49e-85cc88c5269b)

*Ref 1: Python*

Then, I used a with statement to open the file:

![Screenshot 2024-08-02 122229](https://github.com/user-attachments/assets/840e0123-8f8f-4217-86b3-15d3828a913a)

*Ref 2: Python*

In my algorithm, the with statement is used with the .open() function in read mode to open the allow list file for the purpose of reading it. The purpose of opening the file is to allow me to access the IP addresses stored in the allow list file. The with keyword will help manage the resources by closing the file after exiting the with statement. In the code with open(import_file, "r") as file:, the open() function has two parameters. The first identifies the file to import, and then the second indicates what I want to do with the file. In this case, "r" indicates that I want to read it. The code also uses the as keyword to assign a variable named file; file stores the output of the .open() function while I work within the with statement.

## Read the file contents
In order to read the file contents, I used the .read() method to convert it into the string.

![Screenshot 2024-08-02 122550](https://github.com/user-attachments/assets/0c8e3f4c-3ef4-4bfc-a5c6-bb6c59e64592)

*Ref 3: Python*

When using an .open() function that includes the argument "r" for “read,” I can call the .read() function in the body of the with statement. The .read() method converts the file into a string and allows me to read it. I applied the .read() method to the file variable identified in the with statement. Then, I assigned the string output of this method to the variable ip_addresses. 

In summary, this code reads the contents of the "allow_list.txt" file into a string format that allows me to later use the string to organize and extract data in my Python program.

## Convert the string into a list
In order to remove individual IP addresses from the allow list, I needed it to be in list format. Therefore, I next used the .split() method to convert the ip_addresses string into a list:

![Screenshot 2024-08-02 122755](https://github.com/user-attachments/assets/d33eb300-a706-4703-881d-002d8c74e5be)

*Ref 3: Python*

The .split() function is called by appending it to a string variable. It works by converting the contents of a string to a list. The purpose of splitting ip_addresses into a list is to make it easier to remove IP addresses from the allow list. By default, the .split() function splits the text by whitespace into list elements. In this algorithm, the .split() function takes the data stored in the variable ip_addresses, which is a string of IP addresses that are each separated by a whitespace, and it converts this string into a list of IP addresses. To store this list, I reassigned it back to the variable ip_addresses. 

## Iterate through the remove list
A key part of my algorithm involves iterating through the IP addresses that are elements in the remove_list. To do this, I incorporated a for loop:

![Screenshot 2024-08-02 131453](https://github.com/user-attachments/assets/176e3d46-17f0-4d69-87d7-a41f8a9933f6)

*Ref 4: Python*

The for loop in Python repeats code for a specified sequence. The overall purpose of the for loop in a Python algorithm like this is to apply specific code statements to all elements in a sequence. The for keyword starts the for loop. It is followed by the loop variable element and the keyword in. The keyword in indicates to iterate through the sequence ip_addresses and assign each value to the loop variable element. 

## Remove IP addresses that are on the remove list
My algorithm requires removing any IP address from the allow list, ip_addresses, that is also contained in remove_list.  Because there were not any duplicates in ip_addresses, I was able to use the following code to do this:

![Screenshot 2024-08-02 131646](https://github.com/user-attachments/assets/313db178-ee3f-4504-a0ef-59d094c34e54)

*Ref 5: Python*

First, within my for loop, I created a conditional that evaluated whether or not the loop variable element was found in the ip_addresses list. I did this because applying .remove() to elements that were not found in ip_addresses would result in an error. 

Then, within that conditional, I applied .remove() to ip_addresses. I passed in the loop variable element as the argument so that each IP address that was in the remove_list would be removed from ip_addresses.

## Update the file with the revised list of IP addresses 
As a final step in my algorithm, I needed to update the allow list file with the revised list of IP addresses. To do so, I first needed to convert the list back into a string. I used the .join() method for this:

![Screenshot 2024-08-02 131811](https://github.com/user-attachments/assets/67e815dc-2498-4f4a-927f-9c975533269c)

*Ref 6: Python*

The .join() method combines all items in an iterable into a string. The .join() method is applied to a string containing characters that will separate the elements in the iterable once joined into a string. In this algorithm, I used the .join() method to create a string from the list ip_addresses so that I could pass it in as an argument to the .write() method when writing to the file "allow_list.txt". I used the string ("\n") as the separator to instruct Python to place each element on a new line. 

Then, I used another with statement and the .write() method to update the file:

![Screenshot 2024-08-02 131915](https://github.com/user-attachments/assets/5b93ede8-9cc8-44c1-961b-1d0ce69eadb4)

*Ref 7: Python*

This time, I used a second argument of "w" with the open() function in my with statement. This argument indicates that I want to open a file to write over its contents. When using this argument "w", I can call the .write() function in the body of the with statement. The .write() function writes string data to a specified file and replaces any existing file content. 
In this case I wanted to write the updated allow list as a string to the file "allow_list.txt". This way, the restricted content will no longer be accessible to any IP addresses that were removed from the allow list. To rewrite the file, I appended the .write() function to the file object file that I identified in the with statement. I passed in the ip_addresses variable as the argument to specify that the contents of the file specified in the with statement should be replaced with the data in this variable.
