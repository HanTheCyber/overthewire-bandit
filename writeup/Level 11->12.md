# Goal  
The password for the next level is stored  in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.  
# Các bước thực hiện
1. Log in bandit11
2. The data.txt file contents are an encrypted message. The encryption method is called ROT13.  
The ROT13 cipher is a simple substitution cipher where the encryption method is shift each plaintext leter 13 positions in the alphabet to form the ciphertext.  
<img width="412" height="212" alt="image" src="https://github.com/user-attachments/assets/87c5a4d4-3915-4752-a5f2-df833e2b8074" />  

We can use the chart over here to perform the operation, or we can just shift each one of these letters by 13 positions to get the ciphertext. And then the cipher has been applied, it's called the ciphertext  

So if we use this cipher to encrypt the plaintext `hackerfrogs`, the resulting ciphertext would be `unpxresebtf`.  

So, to decypt the ciphertext, we would do the exact same operation, shifting each ciphertext letter by 13 places in the alphabet.  

To solve this problem, we're going to be using the Linux `tr` command. There are different ways we can solve this, but since we are working inside of Linux, we will try to keep on working inside of Linux. And the Linux `tr` command can be used to transform specified characters to other specified characters, and it can be used to simulate ROT13 decryption.  

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```  

So what exactly is this command doing? Frist of all, we read the data.txt file and then we supply a pipe. The pipe is going to provide whatever is the output of the first command, and it is going to provide it as the input for the second command. So, we are using the `tr1 command, we are specifying that all capital letters A to Z, and all lowercase letters a to z are going to be mapped to capital N to capital Z, and then capital A to capital M, and then lowercase n to lowercase z is going to be mapped to uppercase A to uppercase M.  

We get the message here
```bash
GROozWPO8QyN0mGrjUkID0WCYkZiQxrN
```  



