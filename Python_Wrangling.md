# Python Wrangling

I begin the next challenge on my pico gym page, Python Wrangling. Clearly some people don't like this one as it sits at a 62% liked.... Anyways the description states that "python scripts are invoked kind of like programs in the terminal... Can you run this python script using this password to get the flag?". In that sentence the phrases 'this python script', 'this password', and 'the flag' are all blue meaning they link to something of course. 'This python script' downloads a file ende.py. I then also click on 'this password' to receive a file named 'pw.txt'. The phrase 'the flag' downloads a file called 'flag.txt.en'. Well why the hell does this file try and have 2 extensions??? I only see that with malware lol. I first inspect the script in nvim. Well I actually don't know any python so uhhhhh I'm gonna have to google all of this.

### Post googling endeavors

So this script here seems to import the modules `sys` and `base64`. I know base64 is probably for encoding and sys is for cl argument handling. It also imports the Fernet module from the cryptography library. There are 2 ways to use the script. Either with the flag -e to encrypt something or -d to decrypt something. We want to I believe decrypt something. If you encrypt something it encodes it with base64, and creates a Fernet encryption object, and then opens the file in binary mode for reading, encrypts it, and writes the encrypted data to stdout. Decryption is the exact opposite, putting decrypted data in stdout. Basically just a simple script to encrypt-decrypt stuff with.

### My Idea

Well my *assumption* is the file ending for the file 'flag.txt.en' means 'flag.txt' '.en(crypted)' or something like that. So I will decrypt that file using the provided script.

### Running the script

After running 'python ende.py -d flag.txt.en' the script prompts me for a password. Well we were kinda given that previously mentioned pw.txt file so I will just copy and paste that string into here. The password given in pw.txt is: dbd1bea4dbd1bea4dbd1bea4dbd1bea4 . After entering that password string we end up with a string being printed in stdout. Seems to be our answer/flag.
