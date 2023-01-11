# Lab Report 1

*This is a tutorial for incoming CSE 15L students

## Step 1: Download VSCode
This step is pretty straightforward. Go to the [VSCode website](https://code.visualstudio.com), and click the big download button. 
*Make sure that the right os is selected before downloading*
<img width="1470" alt="Screenshot 2023-01-11 at 2 09 05 PM" src="https://user-images.githubusercontent.com/44252902/211929366-eb38506f-dd77-468b-9709-64b04d9812e4.png">

Once VSCode is done downloading, open it up and open the terminal by selecting "Terminal" at the top of your screen and then "New Terminal"
<img width="1470" alt="Screenshot 2023-01-11 at 2 16 19 PM" src="https://user-images.githubusercontent.com/44252902/211929662-f7b6ba4c-82bd-457e-b8c6-09434dce8748.png">

## Step 2: Connecting Remotely
Go to the [account lookup tool](https://sdacs.ucsd.edu/~icc/index.php) and enter you UCSD username and student ID to find your CSE 15 account
It should look like this:
<img width="1470" alt="Screenshot 2023-01-11 at 2 20 03 PM" src="https://user-images.githubusercontent.com/44252902/211930523-a3922421-5124-47d3-a5cc-13fddc8c88be.png">

Write down the gray-boxed text that looks like with cs15lwi23abc where abc is replaced by three other letters. This is your username.
**Henceforth, repalce every instance of cs15lwi23abc in the tutorial with your own username**

If you have not done so yet, use the password reset tool to reset your password (you can use your old password if it satisfies all the requirements)

Now it's time to connect remotely using the VSCode terminal:
* Go to VSCode and type this in the terminal: ssh cs15lwi23abc@ieng6.ucsd.edu
* **Remember, replace cs15lwi23abc with your own username**
* Enter yes when asked if "you want to continue connecting"
* Enter your password when prompted
* Success!
<img width="500" alt="Screenshot 2023-01-11 at 2 28 37 PM" src="https://user-images.githubusercontent.com/44252902/211931824-27201daa-ec52-4698-9d16-1ec577194632.png">

## Step 3: Test Some Commands
Now that you're connect, just treat this like being in any other directory.
You can mess around with all your favorite commands - here are some examples:
* cd
* cat
* pwd
* ls

You can look at a list of usernames if you "% ls" after "% cd .."-ing to your home directory's parent directory:
<img width="979" alt="Screenshot 2023-01-11 at 2 33 37 PM" src="https://user-images.githubusercontent.com/44252902/211932316-be2484db-6a76-404e-b0b3-ce8103ed907c.png">

That's it!
