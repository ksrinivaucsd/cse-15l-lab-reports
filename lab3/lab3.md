## Karthik Srinivasan's CSE 15L Lab 3 Submission

*Part 1*

The bug that we will explore is ArrayExamples' inability to perform the reverseInPlace function.

'''
  @Test 
	public void testReverseInPlace2() {
    int[] input1 = { 3, 2, 1 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 1, 2, 3 }, input1);
	}
 '''
