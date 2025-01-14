# Email-Tables-with-Power-Automate
Data can be presented in various formats, such as images, graphs, or tables. Since data is a valuable asset for any organization, it is crucial to ensure the audience can easily comprehend it.
In this task we are going to use Power Automate, where the data should be extracted, formated in a tabular column and email the same.

Let us see how to convert the data in String sent as a table via Email.


Initialize a variable with your string.
<p align="center">
<img src="https://github.com/user-attachments/assets/17f366ac-fb0a-4ff8-9ee3-846218fe3146" alt=PowerAutomate">
</p>

Declare another variable of type 'array' and using split function, create substrings for each line.
<p align="center">
  <img src="https://github.com/user-attachments/assets/8f66f91c-20e3-4f61-96d6-193a54eea118" alt=PowerAutomate">
</p> 

```
split(variables('inputVariable'), decodeUriComponent('%0A'))
```

Output of the step will create an array
<p align="center">
  <img src="https://github.com/user-attachments/assets/5798d527-ed88-4283-8c15-6439bf89db23" alt=PowerAutomate">
</p>  

Declare a new array variable. Using For-loop, read the contents of the above array and append the contents to the new array variable as a Attribute-Value pair.

This is achieved using Append to Array variable.
<p align="center">
  <img src="https://github.com/user-attachments/assets/2f66913f-4164-446f-934b-bf6e98d00ccd" alt=PowerAutomate">
  <img src="https://github.com/user-attachments/assets/e5d5d1a5-9048-45a9-8f8f-d67390d0440a" alt=PowerAutomate">
</p>  
```
trim(first(split(item(),':')))
trime(replace(item(),concat(first(split(item(),':')),':'),''))
```
