# Email-Tables-with-Power-Automate
Data can be presented in various formats, such as images, graphs, or tables. Since data is a valuable asset for any organization, it is crucial to ensure the audience can easily comprehend it.
In this task we are going to use Power Automate, where the data should be extracted, formated in a tabular column and email the same.

Let us see how to convert the data in String sent as a table via Email.


Initialize a variable with your string.
![image](https://github.com/user-attachments/assets/17f366ac-fb0a-4ff8-9ee3-846218fe3146)


Declare another variable of type 'array' and using split function, create substrings for each line.
```
split(variables('inputVariable'), decodeUriComponent('%0A'))
![image](https://github.com/user-attachments/assets/8f66f91c-20e3-4f61-96d6-193a54eea118)



