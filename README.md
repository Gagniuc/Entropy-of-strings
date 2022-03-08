# Entropy-of-strings


The current JS application calculates the entropy of a string.

The focus of this implementation includes a specialized function called "entropy" which has the text sequence parameter and returns a value that represents entropy.


Entropy measure of the information content of the string, and can be interpreted as the number of bits required to encode each symbol from a string given perfect compression. The entropy value is maximal when each character is equally likely...


In information theory, entropy is a measure of the uncertainty in a random variable. In this context, the term usually refers to the Shannon entropy, which quantifies the expected value of the message's information.
Claude E. Shannon introduced the formula for entropy in his 1948 paper "A Mathematical Theory of Communication."

<img src="https://github.com/Gagniuc/Entropy-of-strings/blob/main/img/entropy%20eq.png?raw=true" height="90" alt="Entropy">

or

<img src="https://github.com/Gagniuc/Entropy-of-strings/blob/main/img/entropy.png?raw=true" height="100" alt="Entropy">

where n represents the total number of symbols in the alphabet of a sequence and
pi represents the probability of occurrence of a symbol i found in the alphabet.

A step-by-step version of the entropy calculation is also shown [here](https://github.com/Gagniuc/Entropy-of-Text).

```js

function entropy(c){

	//ALPHABET DETECTION
	var a = [];
	var t = c.split('');
	var k = t.length;

	for(var i=0; i<=k; i++){
		var q = 1;
		for(var j=0; j<=a.length; j++){
			if (t[i] === a[j]) {q = 0;}
		}
		if (q === 1) {a.push(t[i]);}
	}

	var e = 0;
	var r = '';
	var l = '';

	for(var i=0; i<=a.length-1; i++){
				
		r = c.replace(new RegExp(a[i], 'g'),'').length;
					
		l = a[i];
		a[i]=(k-r)/k;

		//e += -(a[i]*Log(2,a[i]));
		e += (a[i]*Log(2,(1/a[i])));
	}

	return e;
}

function Log(n, v) {
	return Math.log(v) / Math.log(n);
}
```

Live: https://gagniuc.github.io/Entropy-of-strings/

![screenshot](https://github.com/Gagniuc/Entropy-of-strings/blob/main/text_entropy.png?raw=true)


# References

<i>Paul A. Gagniuc. Algorithms in Bioinformatics: Theory and Implementation. John Wiley & Sons, Hoboken, NJ, USA, 2021, ISBN: 9781119697961.</i>
