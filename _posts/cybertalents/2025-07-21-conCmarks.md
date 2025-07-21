---
layout: post
title: "conCmarks"
date: 2025-07-21
categories: [Web]
---

# conCmarks - cybertalents(web)

Brief `it might be useful to find a mark ` 

- to find the mark 
- goals get the flag 

site = ``http://wcamxwl32pue3e6mekgvd1gf9zrqqyz8l9o8u93w-web.cybertalentslabs.com/``
## Recon 

- site says `look around you there might be something`

```html
<!--FILE=> sourceXXXX -->
<!--XXXX are numbers > 7000 & < 9000 --> 

header=R3v3r53Fuck

```


writing sol.py for it 
- gave us this 
- `http://wcamxwl32pue3e6mekgvd1gf9zrqqyz8l9o8u93w-web.cybertalentslabs.com/source8020`

```python 
import requests
import colorama
from colorama import Fore

  
def brute_source():
colorama.init()
url = input(Fore.GREEN + "url: ")
for i in range(7000, 9000):
url = f"{url}{i}"
try:
response = requests.get(url)
if response.status_code == 200:
print(f"found valid source at: {url}" + Fore.GREEN)
else:
print(f"NOt found: {i}" + Fore.RED)
except requests.RequestsException as e:
print(f"error accessing {url}: {e}")

if __name__ == "__main__":
brute_source()
``` 


and curl the site  

```php 
include('flag.php');	


if( @$_GET['n1'] && @$_GET['n2'] )
{
	$input1 = $_GET['n1'];
	$input2 = $_GET['n2'];
	if( $input1 !== $input2 && @hash("md5", $salt.$input1) === @hash("md5", $salt. $input2) )
	{
		echo $flag;

	} else {

		echo "Sorry this value not valid.";
	}
} else{
	exit();
}


```
