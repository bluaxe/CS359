
##1.14

###a

y=10 / (10-9*x)
![Figure](https://raw.github.com/bluaxe/CS359/master/ch01/assets/1.14.a.png)

###b

2= 10/(10 - 9*x)

x= 5/9 ≈ 0.56

So, the percentage needed is about 0.56

###c 

(0.56/10)/(1-0.56+0.56/10) = 1/9 ≈ 0.11111

###d

Maximun speedup = 10 / (10 -9*1) = 10

5 = 10 /(10 - 9*x)

x= 8/9 ≈ 0.89

###e 

When the percentage of vectorization is 70%
Speeup = 10 / (10 - 9*0.7 ) ≈ 2.7 

plus the addtional speedup of 2

4.7 = 10 / (10 - 9*x ) 

x = 0.87


##1.17

###a 

1 / (0.4 /2 + 0.6)  = 1.25

###b

1 / (0.01 + 0.99/2 ) ≈ 1.98

###c

1 / (0.2 + 0.8 * (0.6+ 0.4/2) ) ≈ 1.19

###d 

1/ (0.8 + 0.2 * (0.01 + 0.99/2) ) ≈ 1.11

##2.1

###a

double precision element is 8B and the block size is 64B, it can hold 8 element.
so we can divide the matrix to 4 8x8 matrix, then the minimum size of the cache for 2 8x8 matrix is:

2 x 8 x 8 x 8B = 1KB

###b

#####The block version:

When visiting the 8x8 matrix, each row will evoke one miss, the first column will evoke 8 misses,
but they will be cached up, so ,the totall misses for one 8x8 matrix is:

8 + 8

#####The unblock version

64B block can hold 8 element , when visiting a row of 256 elements, the missrate is 1/8
but when visiting columns, one visit will evoke a miss and after 256 visits of a column,
the 16KB cache is full and next column will evoke misses too.
so the totall misses for one 8x8 matrix is:

8x8+8

so 9 misses for the unblock version compared to 2 misses for the block version.

###c

```
for(int ii=0;i<N;i+=B){
	for(int jj=0;j<N;j+=B){
		for(int i=ii;i<min(N,ii+B);i++){
			for(int j=jj;j<min(N,jj+B);j++){
				output[i][j]=input[j][i];
			}
		}
	}
}
```

###d
2 way set associative.

###e
the result is related to the band width of the l2 cache and the size to l1 cache of the computer.


##2.8

###a

direct-mapped:0.86ns
two-way : 1.12ns
four-way : 1.37ns
so two-way requires 1.12/0.86 = 1.30 times of the direct-mapped.

four-way requires 1.37/0.86 = 1.56 times of the direct-mapped.

###b

16KB : 1.27ns
32KB : 1.35ns
64KB : 1.37ns

So:

The access time of 32KB is 1.35/1.27 ≈ 1.06 of that of 16KB.

The access time of 32KB is 1.37/1.27 ≈ 1.08 of that of 16KB.

###c

#####Miss per referenced instruction :

	DM :   0.006664 / 0.3 ≈ 0.022

	2-Way: 0.00366  / 0.3 ≈ 0.012

	2-Way: 0.009887 / 0.3 ≈ 0.033

	2-Way: 0.000266 / 0.3 ≈ 0.00088


#####Hit Cycles
The cacti access time is 0.5ns

	DM : 	0.87 / 0.5  = 2 cycles

	2-Way : 1.12 / 0.5  = 3 cycles

	4-Way : 1.37 / 0.83 = 2 cycles

	8-Way : 2.03 / 0.79 = 3 cycles


#####Miss Penalty:
	DM : 	10 / 0.5  = 20 cycles

	2-Way : 10 / 0.5  = 20 cycles

	4-Way : 10 / 0.83 = 13 cycles

	8-Way : 10 / 0.79 = 13 cycles

#####AVG Access Time :
	DM : 	0.022 * 20 + (1-0.022) * 2 = 2.3960 * 0.5 = 1.198

	2-Way : 0.012 * 20 + (1-0.012) * 3 = 3.2040 * 0.5 = 1.602

	4-Way : 0.033 * 13 + (1-0.033) * 2 = 2.3630 * 0.83= 1.961

	8-Way : 0.0008* 13 + (1-0.0008)* 3 = 3.0088 * 0.79= 2.377

The lowest is direct-mapped

##2.10

###a
Cycle time : 0.51ns

Access time: 1.12ns

1.12 / 0.51 ≈ 2.19 pipestages

###b

				Area 			Energy per access
	Pipelined	1.19mm^2		0.16nJ
	Banked		1.36mm^2		0.13nJ

The banked design requires more area because it need more circuit to decide wether hit or not,
it consumes less engergy because its active memory arrays are less then the pipelined design.


##2.12
###a
16B

###b

None merging write buffer takes 2 cycles to fill one L2 entry, it ends up taking 8 cycles.

Merging write buffer takes only 4 cycles.

The speedup is 2.

###c

With non-blocking caches, write request can be process from the write buffer,
it result in needing less entries.

#Practices

##2.1

![Figure2.1](https://raw.github.com/bluaxe/CS359/master/practices/assets/2.1.jpg)


##2.2

###a

![Figure2.2.a](https://raw.github.com/bluaxe/CS359/master/practices/assets/2.2.a.jpg)

###b

![Figure2.2.b](https://raw.github.com/bluaxe/CS359/master/practices/assets/2.2.b.jpg)

##2.3

###a

![Figure2.3.a](https://raw.github.com/bluaxe/CS359/master/practices/assets/2.3.a.jpg)

###b

![Figure2.3.b](https://raw.github.com/bluaxe/CS359/master/practices/assets/2.3.b.jpg)

##2.4

###a

![Figure2.4.a](https://raw.github.com/bluaxe/CS359/master/practices/assets/2.4.a.jpg)

###b

![Figure2.4.b](https://raw.github.com/bluaxe/CS359/master/practices/assets/2.4.b.jpg)

##2.5

![Figure2.5](https://raw.github.com/bluaxe/CS359/master/practices/assets/2.5.jpg)

