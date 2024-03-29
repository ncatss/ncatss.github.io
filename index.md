## Learning Log
<details>
  <summary>08/05/2019 | Mutex</summary>
</details>

_What it's doing:_
* a mutex is locking mechanism used to synchronize access to a resource. it makes multi-threads taking turns to access same resource. (to prevent multiple-threads from accessing the same memory)

_Why?_
(the reordering of memory access and lack atomicity in large data structures)
* CPU doesn’t concern itself with data structures, it only concerns itself with primitive types. So the actions of writing big data structure are not atomic.
* CPU changes the order in which data is written and read from that cache.(so mutex has a fence).

_Things to be carefully about:_
* a recursion mutex can be locked more than once. but if it's non-recursion mutex --> If a thread which had already locked a mutex, tries to lock the mutex again, it will enter into the waiting list of that mutex, which results in deadlock. 

&nbsp;
<details>
  <summary>08/04/2019 | Store Passward Safely</summary>
</details>

_Basic Ideas:_
  
* hash --> password can not be directly read; 
           don't show information about password length etc.
* salt --> people cannot just generate hashcode dictionary for common password to do comparison directly;
           same password transfer to different hashcode for different user
* stretching --> to slow down offline attacks. 
                 (they can keep moving forwards for a hashcode or generate values for salt (from AA to ZZ)

  
_Steps:_

* Use a strong random number generator to create a salt of 16 bytes or longer. 
  (use CryptoAPI on Windows or /dev/urandom on Unix-like systems)

* Feed the salt and the password into the PBKDF2 algorithm.
	* Use HMAC-SHA-256 as the core hash inside PBKDF2. (SHA-256 better than MD5 or SHA-1, since those proven giving same hash for 2 different data)
		1. take random key K; flip some bits, giving K1;  
		2. compute SHA-256 hash for K1 + password, giving H1;  
		3. flip a different set of bits in K, giving K2;  
		4. compute SHA-256 hash for K2 + H1, giving final hash H2.  
	* Perform 80,000 iterations or more [March 2019]. (Increase iteration count regularly to keep up with faster cracking tools)
	* Take 32 bytes (256 bits) of output from PBKDF2 as the final password hash.
  
* Store the iteration count, the salt and the final hash in your password database.

[Reference Details](https://nakedsecurity.sophos.com/2013/11/20/serious-security-how-to-store-your-users-passwords-safely/)


&nbsp;
## Links

my favorite [music](https://open.spotify.com/album/0S0KGZnfBGSIssfF54WSJh)

[movie](https://www.imdb.com/title/tt2283336/) I'm going to watch tmr

ask any question to [Google!](https://www.google.com/)

[maps](https://www.google.com/maps) I used the most

text to ASCII Art [Generator](http://patorjk.com/software/taag/#p=display&f=Graffiti&t=Type%20Something%20)


&nbsp;
## Plans

all my hardworks

```markdown

- workout hard

- work hard

- learn hard

- play hard

- eat hard

- sleep hard

- love myself hard

- love my dog too

```


&nbsp;
## Support or Contact

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
