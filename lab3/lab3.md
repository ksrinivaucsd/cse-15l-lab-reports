## Karthik Srinivasan's CSE 15L Lab 3 Submission

*Part 1*

The bug that we will explore is ArrayExamples' inability to perform the reverseInPlace function.

The following test fails.

	  @Test 
		public void testReverseInPlace2() {
	    int[] input1 = { 3, 2, 1 };
	    ArrayExamples.reverseInPlace(input1);
	    assertArrayEquals(new int[]{ 1, 2, 3 }, input1);
		}

The following test does not fail.

		@Test 
		public void testReverseInPlace() {
	    int[] input1 = { 3 };
	    ArrayExamples.reverseInPlace(input1);
	    assertArrayEquals(new int[]{ 3 }, input1);
		}
  
The following is the symptom as the test result of the buggy code.

![Image](CSE15LLab3Pic1.png)

The following is the buggy code.

	  static void reverseInPlace(int[] arr) {
	    for(int i = 0; i < arr.length; i += 1) {
	      arr[i] = arr[arr.length - i - 1];
	    }
	  }

The following is the code after bug-removal.

	static void reverseInPlace(int[] arr) {
	  for (int i = 0; i < arr.length / 2; i++) {
	    int temp = arr[i];
	    arr[i] = arr[arr.length - i - 1];
	    arr[arr.length - i - 1] = temp;
	  }
	}
