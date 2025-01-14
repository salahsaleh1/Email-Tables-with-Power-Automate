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

<p align="center">
  <img src="https://github.com/user-attachments/assets/b84feec7-89df-4964-bf4a-dc217226450c" alt=PowerAutomate">
</p>  

Next step is creating an HTML table and setting the Columns as automatic.


<p align="center">
  <img src="https://github.com/user-attachments/assets/931a4ec9-45ba-447c-83f1-1aba0a110589" alt=PowerAutomate">
</p> 
It is also possible to choose the columns
<p align="center">
  <img src="https://github.com/user-attachments/assets/7c882f5a-e30d-4957-bace-1b1cbed9a813" alt=PowerAutomate">
</p> 

```
variables('ReadSplit')[0]['Value']
variables('ReadSplit')[1]['Value']
variables('ReadSplit')[2]['Value']
```

The output of the HTML table generates a table without proper format.
In order to decorate with border, use a compose function and add the below css

```
<style>
Table {
  font-family: Arial, Helvetica, sans-serif;
  background-color: #EEEEEE;
  border-collapse: collapse;
  width: 100%;
}

Table td, Table th {
  border: 1px solid #ddd;
  padding: 3px 3px;
}

Table th {
  font-size: 15px;
  font-weight: bold;
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  background-color: #1C6EA4;
  color: white;
}
</style>
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/08205323-1aee-41f3-8faf-ca63252dfc99" alt=PowerAutomate">
</p> 


In the 'Send an Email' action, add the output of 'Compose' and output of 'HTML' action.

<p align="center">
  <img src="https://github.com/user-attachments/assets/55ab776d-3695-4e53-9fed-31c497873273" alt=PowerAutomate">
</p> 

