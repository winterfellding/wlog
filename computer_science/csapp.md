##### Big-endian, little-endian

	在内存中从一个数据从高地址位向低地址位是little－endian
	反之，则是big－endian，
	例如，一个数据是12345678
	0x100 0x101 0x102 0x103
	12		34	  56    78    这个就是big－endian
	78		56	  34    12    这个就是little－endian
	
	intel处理器一般都为little－endian，IBM，sun 一般都是big－endian，最近的处理器也有bi－endian的，就是两种都支持。
	
	不同处理器处理int float这些数据时，由于big－endian和little－endian，完整数据是一样的，但在地址上的排列会不同，pointer则各个系统都不同。