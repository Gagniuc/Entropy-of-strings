# Entropy-of-strings

It is a measure of the information content of the string, and can be interpreted as the number of bits required to encode each character of the string given perfect compression. The entropy is maximal when each character is equally likely...

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
