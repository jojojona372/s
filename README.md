# README
## XSteam shortcut for Matlab
This script makes it possible to use XSteam on arrays, too. Also, it's shorter to
type 's(...)' than to type 'XSteam(...)' every time.

## Download instructions
Go to [this page](https://raw.githubusercontent.com/jojojona372/s/main/s.m), and right-click. Then select "save as", and save the file somewhere.

## Install instructions
Download `s.m`, and place it in the folder that you'd like to use.
Next, use the command `pathtool` in Matlab to add the folder that you placed `s.m` in, to your Matlab path.

# How to use
## As a shortcut
`s()` can be used as a shortcut for `XSteam()`, since typing "s" is a lot
faster than typing "XSteam" every time.
You can use it the same way you use XSteam, but instead of `XSteam(...)`
you write `s(...)`.


For example:  
```
XSteam('Tsat_p',1)  
XSteam('h_pT',1,50)  
```
Becomes:  
```
s('Tsat_p',1)  
s('h_pT',1,50)  
```

## For arrays
I think this is the most useful application of this function. It also allows
you to put in arrays instead of single values. This means you don't have
to write a for loop every time you want to process an array using XSteam.
All you have to do is replace the variables with a single value with a
variable that is an array.


For example:  
```
P = [0.1,1,20,50];  
T = [0.1,1,10];  
s('h_pt',P,T);  
```
This will give a 4x3 array as output. This is very useful for quickly
generating large amounts of data.

## Streams
s() uses a 4th input argument called 'streams'. This is useful when you have
2 arrays that are the same length, and you want to combine them to have a
single output array. This is useful when you have data about a number of
streams, with unique values for each property. (temperature, pressure,
enthalpy, etc.)


For example:  
```
P = [4,  154, 108];
T = [120, 88, 317];
enthalpy = s('h_pt',P,T,1);
```
Will return:  
```
enthalpy = 
503.926050449991
380.505390342921
2712.61142484220
```
This will return a single array with the enthalpy per stream. You will
notice the `1` as the 4th input argument. By setting this to `0`, it will
function the same as when leaving the 4th input argument out, without
treating the inputs values as streams.
