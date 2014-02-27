##### Where storge lives
	1. Registers 			in the processor
	2. Stack     			only slower than registers, obj refrence in there, and obj themselves on there (in RAM)
	3. Heap      			The objects lives here (also in the RAM)
	4. Constant storage		Consts can not be changed, so they may be put in ROM 
	5. Non-RAM storage     could be file transferred to stream object
	
##### Special Cases
	primitive types
	These can not be created with "new"
	boolean, byte, short, int, long, float, double, char, void
	These types have "warpper" classes for them, which are
	Boolean, Byte, Short, Int, Long, Float, Double, Character
	
##### High-precision numbers

	BigInteger & BigDecimal // these two class are for solving problem which cause by IEEE float problem, the calculation may be not right
	 

##### Collections

	// convert java.util.Enumeration to java.util.List
	Collections.list(e);
	// convert java.util.List to java.util.Enumeration
	Collections.enumeration(l)
	// 
	Collections.nCopies(int n, T o) // return an inner class CopiesList
	Collections.fill(List list, T obj) // replace all the element in the collection to the obj
	

##### Arrays
	
	Arrays.sort // there's a const in the String named CASE_INSENSITIVE_ORDER,
	can be used as an param in the sort method
	Arrays.sort(list, String.CASE_INSENSITIVE_ORDER);
