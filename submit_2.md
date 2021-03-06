##2.16
Instructions per second:

	8 x 3*10^9 / 2 = 1.2*10^10

L2 Miss per second :

	1.2*10^10 * 6.67 / 1000 = 80040000

Data per second :

	80040000 * 32 byte = 2561.3 MB/s

Max :

	2561.3 MB/3 x 2 = 5122.6 MB/s

Since DDR2-667 BandWidth is 5336 MB/s, larger than 5122.6 MB/s

One is enough

##2.18
###a
	Precharge Time 	:	Tprc = 5 x (1/333MHz) = 15ns
	Activation Time	: 	Tact = 5 x (1/333MHz) = 15ns
	Column Select Time : 	Tcst = 4 x (1/333MHz) = 12ns

####Police 1 

	Hit Time 		: Th = r(Tcst + Tddr)
	Miss Time		: Tm = (1-r)(Tprc + Tact + Tcst)

####Police 2

	Time 	: T = Tact + Tcst + Tddr

When Police 1 's access time equals Police 2's 

	r(Tcst + Tddr) + (1-r)(Tprc + Tact + Tcst) = Tact + Tcst + Tddr

so r = 0.5

when r < 0.5 Police 2 is beter , otherwise Police 1 is beter.

###b
When the accesses comes without delay, we must count the precharge time.
so we have:

	r(Tcst + Tddr) + (1-r)(Tprc + Tact + Tcst) = 0.9*(Tact + Tcst + Tddr) + 0.1(Tprc + Tact + Tcst + Tddr)

so r = 0.45 


###c 
If hits, Policy 2 needs (2 + 4)nJ per access so Policy 2 requires 6r nJ per access. r is the hit rate.

#2.(1)
### U盘和SSD均为 NAND flash, 它们的工作原理为:
NOR Flash 每个存储单元的晶体管与标准的场效应管相似，但是每个单元具有
2 个栅极（控制栅极和浮置栅极）。NOR Flash 的读操作与一般的RAM 相似，可以
随机地对任意地址进行读操作。适合于存储程序代码，例如BIOS 代码。存储数据
时电流从源极流向漏极，擦除数据时在源极与控制栅极之间施加较强的电压，将浮
置栅极上的电荷吸出。NOR Flash 写入时间需要200us 左右，而擦除过程比较复杂，
是一个比较慢的过程，通常需要在软件的控制下进行，块擦除的时间约需要0.5s。

NAND Flash采用串行的晶体管连接结构，每个存储单元包括多个晶体管，构成多个存储位。
这种电路结构使得晶体管之间的间隔可以做的很小，芯片的集成度更高。
由于每个单元数据量更大，NAND具有较快的擦写速度和较低的成本，允许擦写的次数更多。
但是，NAND Flash的访问时顺序式的，读写操作以一个数据单元（page）为单位进行，
而数据的擦出以块为单位，一个块包括若干页。NAND的读取时间约为60us，擦除时间每块2ms。

总而言之， 总而言之， NOR Flash 的读写方式更类似与内存，但是速度慢集成低；
而NAND flash的读写方式类似于硬盘，但是速度比Nor 快，拥有更大的储存单元，更高的集成度。

> 部分内容来源于《嵌入式系统原理与实验》

#2.(2)
###PCM优点
####1.高存取速度
由于相变存储材料的晶化速度一般在50ns以下，因此相变存储器拥有很高的写入速度。从目前已经量产的产品性能来看，PRAM可以达到NAND型闪存的写入速度水平，但与NAND和NOR闪存不同的是，PRAM存储器写入新数据不需要擦除过程，更加快了写入数据的速度。

####2. 非易失性
PRAM是一种非易失性随机存储器，由于数据是以相变形式保存，除非受到高温，超过晶化温度，数据才会被破坏。相变材料的使用寿命则高达1012～1015次写入以上，而闪存的读写寿命仅为10万次左右，即使是SRAM和DRAM，也难以达到这样高的读写次数。此外，PRAM也不象硬盘那样有脆弱的机械部分，不用担心跌落等意外事件对数据造成损失。

####3. 工艺简单
PRAM可以用现有的CMOS工艺进行加工，只需增加2~4次掩模工艺即可。相变材料的成本也较低，加工也很容易。

####4. 高容量
在随机存储器中，SRAM和DRAM的存储密度都非常小，与它们相比，PRAM具有明显的优势。相变存储元件还可以堆叠起来，形成多个存储层。

####5. 缩放比例
NOR和NAND存储器的结构导致存储器很难缩小体型。这是因为门电路的厚度是一定的，它需要多于10V的供电，CMOS逻辑门需要1V或更少。这种缩小通常被成为摩尔定律，存储器每缩小一代其密集程度提高一倍。随着存储单元的缩小，GST材料的体积也在缩小，这使得PCM具有缩放性。

###PCM发展历史
二十世纪五十年代至六十年代，Dr. Stanford Ovshinsky开始研究无定形物质的性质。
1970年9月28日Dr. Stanford Ovshinsky 在Electronics发布文章描述了世界上第一个256位半导体相变存储器。
Intel开发的相变存储器使用了硫属化物（Chalcogenides），这类材料包含元素周期表中的氧/硫族元素。Numonyx的相变存储器使用一种含锗、锑、碲的合成材料（Ge2Sb2Te5），多被称为GST。现今大多数公司在研究和发展相变存储器时都都使用GST或近似的相关合成材料。
业内有人预计在2016年前都不会出现PCMPCM 产品，届时闪存技术的发展可能将PCMPCM 的优势消弭于无形。 

> 部分内容摘自《新电脑》杂志

##3.1 0x027c

###A. Virtual address format
	13 12 11 10 9 8 7 6 5 4 3 2 1 0
	 0  0  0  0 1 0 0 1 1 1 1 1 0 0

###B. Address translate
	VPN					09
	TLB index			1
	TLB tag				02
	TLB hit(Y/n)		N
	Page fault?(Y/N)	N
	PPN					17

###C. Physical address format
	0x17
	11 10 9 8 7 6 5 4 3 2 1 0	
	 0 	1 0 1 1 1 1 1 1 1 0 0

###D. Physical memory reference
	Byte offset			0
	Cache index			F
	Cache tag			17
	Cache hit?(Y/n)		N
	Cache Byte returned	-

##3.2 0x03a9

###A. Virtual address format
	13 12 11 10 9 8 7 6 5 4 3 2 1 0
	 0  0  0  0 1 1 1 0 1 0 1 0 0 1

###B. Address translate
	VPN					0E
	TLB index			2
	TLB tag				03
	TLB hit(Y/n)		N
	Page fault?(Y/N)	N
	PPN					11

###C. Physical address format
	0x17
	11 10 9 8 7 6 5 4 3 2 1 0	
	 0 	1 0 0 0 1 1 0 1 0 0 1

###D. Physical memory reference
	Byte offset			1
	Cache index			A
	Cache tag			11
	Cache hit?(Y/n)		N
	Cache Byte returned	-


##3.3 0x0040

###A. Virtual address format
	13 12 11 10 9 8 7 6 5 4 3 2 1 0
	 0  0  0  0 0 0 0 1 0 0 0 0 0 0

###B. Address translate
	VPN					01
	TLB index			1
	TLB tag				00
	TLB hit(Y/n)		N
	Page fault?(Y/N)	Y
	PPN					-

