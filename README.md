[![Build Status](https://travis-ci.org/Funz/plugin-R.png)](https://travis-ci.org/Funz/plugin-R)

# Funz plugin: R

This plugin is dedicated to launch R calculations from Funz.
It supports the following syntax and features:

  * Input
    * file type supported: *.R, any other format for resources
    * parameter syntax: 
      * variable syntax: `?[...]`
      * formula syntax: `!{...}`
      * comment char: `#`
    * example input file:
<pre class="highlight"><code>branin <- function(x) {
	x1 <- x[1]*15-5   
	x2 <- x[2]*15     
	(x2 - 5/(4*pi^2)*(x1^2) + 5/pi*x1 - 6)^2 + 10*(1 - 1/(8*pi))*cos(x1) + 10
}

cat('z=',branin(c( <font style="background-color:rgb(255,200,0)">?[x1~[1,2]]</font> , <font style="background-color:rgb(255,200,0)">!{?x2 + 1.23 | #.###}</font> )),"\n")</code></pre><br/>Will identify input:
      * x1, expected to vary inside [1,2]
      * x2, expected to vary inside [0,1] (by default)

  * Output
    * file type supported: *.Rout
    * read any named value printed with '=', like `cat('z=',1.234,"\n")`
    * example output file:
<pre class="highlight"><code>> branin <- function(x) {
+ 	x1 <- x[1]*15-5   
+ 	x2 <- x[2]*15     
+ 	(x2 - 5/(4*pi^2)*(x1^2) + 5/pi*x1 - 6)^2 + 10*(1 - 1/(8*pi))*cos(x1) + 10
+ }
> 
> cat('z=',branin(c( 0.5 , 0.132 )),"\n")
z= 3.000715 
> 
> 
> proc.time()
utilisateur     système      écoulé 
      0.152       0.013       0.152 </code></pre><br/>Will return output:
      * z=3.000715 


![Analytics](https://ga-beacon.appspot.com/UA-109580-20/plugin-R)
