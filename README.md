# Simple Serial Comms

Simple Serial Test is an application to test "Simple Serial" ... Surprise...


## Installation

git clone --recursive.

##Compilation

This is a cmake project.

Simply run following commands

```bash
cmake .
make
```


## TEST

You can create virtual serial port by using
 
```bash
socat -d -d pty,raw,echo=0 pty,raw,echo=0
```

and use minicom to interact and test
 
```bash
minicom -D /dev/pts/<port number> 
```



## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License
[MIT](https://choosealicense.com/licenses/mit/)
