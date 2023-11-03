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

The problem with the previous code was that the array was being iterated over while its elements were being swapped. Consequently, elements were being duplicated. The second method only goes through half the array and assigns an iteration that is about to be deleted to temp. This prevents duplication of iterations and lost data.

*Part 2*

The command that I will be exploring is the find command. I have used this (https://www.youtube.com/watch?v=skTiK_6DdqU) YouTube video to learn about the command.

The first argument I will be exploring is name.

Consider the following command.

	find -name chapter-1.txt

Output: 

	./911report/chapter-1.txt
 
 The command takes the name of the file that needs to be found and outputs the path of the file relative to the current working directory. This is useful in locating files.

 Consider the second command.

	 find ./911report -name *.txt

  Output:

	 ./911report/chapter-1.txt
	./911report/chapter-10.txt  
	./911report/chapter-11.txt  
	./911report/chapter-12.txt  
	./911report/chapter-13.1.txt
	./911report/chapter-13.2.txt
	./911report/chapter-13.3.txt
	./911report/chapter-13.4.txt
	./911report/chapter-13.5.txt
	./911report/chapter-2.txt
	./911report/chapter-3.txt
	./911report/chapter-5.txt
	./911report/chapter-6.txt
	./911report/chapter-7.txt
	./911report/chapter-8.txt
	./911report/chapter-9.txt
	./911report/preface.txt

 The previous command finds all the .txt files in the directory 911 report which exists under technical. This is useful when the all the files of a certain type must be found.

 The second argument in find that I will be exploring is the -type argument.

 The type argument is very useful for finding all the files or directories in the current directory. Consider the following code.

	 find . -type d

Output:

	.
	./911report
	./biomed
	./government
	./government/About_LSC
	./government/Alcohol_Problems
	./government/Env_Prot_Agen
	./government/Gen_Account_Office
	./government/Media
	./government/Post_Rate_Comm
	./plos

The previous command found all the subdirectories to the current working directory (technical). This is useful as it shows where one can change directories into.

Another example of the -type argument in the find command is as follows:

	find 911report -type f

 Output:

	 911report/chapter-1.txt
	911report/chapter-10.txt
	911report/chapter-11.txt
	911report/chapter-12.txt
	911report/chapter-13.1.txt
	911report/chapter-13.2.txt
	911report/chapter-13.3.txt
	911report/chapter-13.4.txt
	911report/chapter-13.5.txt
	911report/chapter-2.txt
	911report/chapter-3.txt
	911report/chapter-5.txt
	911report/chapter-6.txt
	911report/chapter-7.txt
	911report/chapter-8.txt
	911report/chapter-9.txt
	911report/preface.txt

 The above command finds all the files in the folder 911report. This is useful for navigating and maintaining a directory.

 The next command line option for find I will explore is the -exec option.

 The exec option executes a command on the files found. Consider the following command.

	 find 911report/ -type f -exec cat {} +
  
  The output for this command is too long but essentially it applies the cat command to every file found in the 911report/ directory. Consequently, every file in the 911report directory is printed to the terminal. This is very useful in order to read multiple different files in the same directory.

Consider another example of the -exec option.

	find 911report/ -type f -exec grep "Clinton" {} +

 This option searches for all the mentions of the string "Clinton" in the 911report/ directory. 

 Output:

	 find 911report/ -type f -exec grep "Clinton" {} +
	911report/chapter-11.txt:            Whatever the weaknesses in the CIA's portraiture, both Presidents Bill Clinton and
	911report/chapter-11.txt:                experts. In 1996, as a result of the TWA Flight 800 crash, President Clinton created
	911report/chapter-11.txt:                plane. One, a December 4 Presidential Daily Briefing for President Clinton
	911report/chapter-11.txt:                is worth noting that they were made by the Clinton administration under extremely     
	911report/chapter-11.txt:                impeachment. In addition, in 1998-99 President Clinton was preparing the government   
	911report/chapter-11.txt:            Officials in both the Clinton and Bush administrations regarded a full U.S. invasion      
	911report/chapter-11.txt:                We have found no indication that President Clinton was offered such an intermediate   
	911report/chapter-11.txt:                already discussed. Since we believe that both President Clinton and President Bush    
	911report/chapter-11.txt:            Earlier chapters describe in detail the actions decided on by the Clinton and Bush        
	911report/chapter-11.txt:                that consumed considerable time-especially in the Clinton administration- and
	911report/chapter-11.txt:                for action offered to both President Clinton and President Bush.
	911report/chapter-11.txt:                threatening the United States. The Clinton administration effectively relied on the   
	911report/chapter-11.txt:                2000, as part of a millennium after-action review. President Clinton and his
	911report/chapter-11.txt:                the FBI, yet during almost all of the Clinton administration the relationship
	911report/chapter-12.txt:                education and employment sharply limited. President Clinton offered us a perceptive   
	911report/chapter-13.3.txt:            2. On President Clinton's tasking the NSC, see Richard Clarke interview (Dec. 18,       
	911report/chapter-13.3.txt:                Department of State During the Clinton Presidency (1993-2001),"undated (online at   
	911report/chapter-13.3.txt:            99. President Clinton, "Address to the Nation on the Strike on Iraqi Intelligence       
	911report/chapter-13.3.txt:            100. President Clinton, "Address Before a Joint Session of the Congress on the State    
	911report/chapter-13.3.txt:                of the Union," Jan. 24, 1995; President Clinton,"Message to the Congress
	911report/chapter-13.3.txt:                Clinton, "Message to the Congress Transmitting Proposed Legislation To Combat       
	911report/chapter-13.3.txt:            102. President Clinton, "Remarks by the President in a Congressional Meeting," July     
	911report/chapter-13.3.txt:            103. President Clinton, "Remarks Announcing the Second Term National Security Team      
	911report/chapter-13.3.txt:            105. President Clinton, "Commencement Address at the United States Naval Academy in     
	911report/chapter-13.3.txt:                prior to 9/11, see President Clinton, "Commencement Address at the United States    
	911report/chapter-13.3.txt:                Naval Academy in Annapolis, Maryland,"May 22,1998; President Clinton,"Keeping       
	911report/chapter-13.3.txt:            President Clinton, in a February 2002 speech to the Long Island Association, said       
	911report/chapter-13.3.txt:                there was no indictment. President Clinton speech to the Long Island Association,   
	911report/chapter-13.3.txt:                Clinton told us that Sudan never offered to turn Bin Ladin over to the United       
	911report/chapter-13.3.txt:                States. President Clinton meeting (Apr.8, 2004). Berger told us that he saw no      
	911report/chapter-13.3.txt:            In February 1997, the Sudanese sent letters to President Clinton and Secretary of       
	911report/chapter-13.3.txt:            42. President Clinton meeting (Apr. 8, 2004); Samuel Berger interview (Jan. 14,
	911report/chapter-13.3.txt:                balance, they think the CIA claim was valid. See also President Clinton meeting     
	911report/chapter-13.3.txt:            51. Samuel Berger interview (Jan. 22, 2004). President Clinton told us that he had      
	911report/chapter-13.3.txt:                embassy bombings. President Clinton meeting (Apr. 8, 2004). See also William Cohen  
	911report/chapter-13.3.txt:                Shelton interview (Feb. 5, 2004); President Clinton meeting (Apr. 8, 2004); Samuel  
	911report/chapter-13.3.txt:                most economic and military assistance to Pakistan. Clinton administration officials 
	911report/chapter-13.3.txt:            79. White House reports made available to the Commission. President Clinton met with    
	911report/chapter-13.3.txt:                June 16, 1999; Samuel Berger interview (Jan. 14, 2004); President Clinton meeting   
	911report/chapter-13.3.txt:            98. President Clinton meeting (Apr. 8, 2004); DOS memo, Sheehan to Albright, "S/CT      
	911report/chapter-13.3.txt:            99. Samuel Berger interview (Jan. 14, 2004); President Clinton meeting (Apr. 8,
	911report/chapter-13.3.txt:                CIA memo, Gordon to Berger, Dec. 21, 1998; NSC memo, Berger to President Clinton,   
	911report/chapter-13.3.txt:            123. NSC memo, Berger to President Clinton, Dec. 24,1998; Randy Moss interview
	911report/chapter-13.3.txt:            124. NSC memo, Berger to President Clinton, Dec. 24, 1998; Janet Reno interview (Dec.   
	911report/chapter-13.3.txt:            128. See President Clinton meeting (Apr. 8, 2004); Samuel Berger interview (Jan. 1,     
	911report/chapter-13.3.txt:            129. James Baker interview (Feb. 4, 2004); President Clinton meeting (Apr. 8, 2004).    
	911report/chapter-13.3.txt:            145. President Clinton meeting (Apr. 8, 2004); William Cohen interview (Feb. 5,
	911report/chapter-13.3.txt:                Clinton to bin Zayid, July 23, 1999; DOS memo, Sheehan to Albright, "Signs of       
	911report/chapter-13.3.txt:                President Clinton in October, however, are slightly different: CTC had helped render911report/chapter-13.3.txt:                letter, Tenet to President Clinton, "CIA's Counterterrorism Efforts,"Oct. 16, 1999. 
	911report/chapter-13.4.txt:            1. President Clinton was a voracious reader of intelligence. He received the
	911report/chapter-13.4.txt:                movements. Berger told us he would tell President Clinton if there was anything in  
	911report/chapter-13.4.txt:            2. President Clinton spoke of terrorism in numerous public statements. In his August    
	911report/chapter-13.4.txt:                from biological and chemical weapons. President Clinton repeatedly linked terrorist 
	911report/chapter-13.4.txt:                Clinton remarks,"On Keeping America Secure for the 21st Century," Jan. 22, 1999 (at 
	911report/chapter-13.4.txt:            3. President Clinton spoke of the Y2K computer problem in his January 19, 1999, State   
	911report/chapter-13.4.txt:            12. NSC memo, Berger to President Clinton, Dec. 9, 1999.
	911report/chapter-13.4.txt:                wrote President Clinton that the State Department's warning seemed to barely        
	911report/chapter-13.4.txt:                register with the Taliban. See NSC memo, Berger to President Clinton, terrorist     
	911report/chapter-13.4.txt:            29. NSC memo, Berger to President Clinton, terrorism threat at the millennium, Dec.     
	911report/chapter-13.4.txt:            32. NSC memo, Berger to President Clinton, terrorist threat at the millennium, Dec.     
	911report/chapter-13.4.txt:                Clinton visited Pakistan; this information was deemed credible by early March. The  
	911report/chapter-13.4.txt:                Meeting on Clinton Trip to South Asia;" NSC email, Kurtz to Berger, two new threats 
	911report/chapter-13.4.txt:            64. President Clinton meeting (Apr. 8, 2004). President Clinton told us he offered      
	911report/chapter-13.4.txt:                front of additional aides. Berger told that President Clinton did not want to press 
	911report/chapter-13.4.txt:            72. The CIA appears to have briefed President Clinton on its "Next Steps and New        
	911report/chapter-13.4.txt:                (for the President); NSC email, Cressey to Berger,"CT Briefing for Clinton," Feb. 8,911report/chapter-13.4.txt:                that one of five goals by the end of the Clinton administration was to secure       
	911report/chapter-13.4.txt:                SacredTerror (Random House, 2002), p. 318. President Clinton confirmed that he made 
	911report/chapter-13.4.txt:                this statement. President Clinton meeting (Apr. 8, 2004).
	911report/chapter-13.4.txt:            110. President Clinton meeting (Apr. 8, 2004); Hugh Shelton interview (Feb. 5, 2004);   
	911report/chapter-13.4.txt:                Clinton).
	911report/chapter-13.4.txt:                Clinton, update on Cole attack, Oct. 12, 2000. For McLaughlin's statement, see John 
	911report/chapter-13.4.txt:                the Clinton administration's deliberations about the Cole in Richard Miniter, Losing911report/chapter-13.4.txt:                Bin Laden: How Bill Clinton's Failures Unleashed Global Terror (Regnery, 2003),     
	911report/chapter-13.4.txt:                memo, Berger to President Clinton, update on Cole investigation, Nov. 25, 2000.     
	911report/chapter-13.4.txt:                memo, Berger to President Clinton, update on Cole investigation, Nov. 25, 2000.     
	911report/chapter-13.4.txt:            137. President Clinton meeting (Apr. 8, 2004).
	911report/chapter-13.4.txt:                Berger to President Clinton, USS Cole investigation update, Nov. 25, 2000.
	911report/chapter-13.4.txt:                briefing Berger, see NSC memo, Berger to President Clinton, USS Cole investigation  
	911report/chapter-13.4.txt:            142. NSC memo, Berger to President Clinton, USS Cole investigation update, Nov. 25,     
	911report/chapter-13.4.txt:            146. President Clinton meeting (Apr. 8, 2004); Samuel Berger interview (Jan. 14,        
	911report/chapter-13.4.txt:                implementation" so late in the Clinton administration. He also questioned the       
	911report/chapter-13.4.txt:                come back to either President Clinton or PresNOTES TO CHAPTER 6 509 ident Bush and  
	911report/chapter-13.4.txt:            159. President Clinton meeting (Apr. 8, 2004).
	911report/chapter-13.4.txt:                Commission, Zelikow has recused himself from our work on the Clinton-Bush transition911report/chapter-13.5.txt:                Clinton administration, up to 25 people received the PDB. In the Bush
	911report/chapter-13.5.txt:            20. President Clinton meeting (Apr. 8, 2004).
	911report/chapter-3.txt:            President Bill Clinton ordered his National Security Council to coordinate the
	911report/chapter-3.txt:                President Clinton, his principal advisers, the Congress, nor the news media felt       
	911report/chapter-3.txt:            FBI Organization and Priorities In 1993, President Clinton chose Louis Freeh as the        
	911report/chapter-3.txt:                support of the Clinton administration, doubled the number of Border Patrol agents      
	911report/chapter-3.txt:                President Clinton appointed George Tenet as DCI in 1997, and by all accounts
	911report/chapter-3.txt:                congressional opposition prevented President Clinton's first secretary of state,       
	911report/chapter-3.txt:                Congress, President Clinton soon ordered the withdrawal of U.S. forces. "Black Hawk    
	911report/chapter-3.txt:                counterterrorism. By the end of President Clinton's first term, this official had      
	911report/chapter-3.txt:            This lesson was applied, using Tomahawk missiles, early in the Clinton
	911report/chapter-3.txt:                President Clinton not only ordered precautions to protect Bush but asked about
	911report/chapter-3.txt:                directives, differently labeled by each president. For President Clinton, they were    
	911report/chapter-3.txt:                national security advisor. When President Clinton took office, he decided right away   
	911report/chapter-3.txt:            President Clinton's first national security advisor, Anthony Lake, had retained from       
	911report/chapter-3.txt:                Clarke. President Clinton and Lake turned to Clarke to do the staff work for them in   
	911report/chapter-3.txt:                the plot to kill President Bush, President Clinton stated:"From the first days of      
	911report/chapter-3.txt:            In his State of the Union message in January 1995, President Clinton promised
	911report/chapter-3.txt:                Veigh and Terry Nichols. President Clinton proposed to amend his earlier proposals     
	911report/chapter-3.txt:            President Clinton issued a classified directive in June 1995, Presidential Decision        
	911report/chapter-3.txt:                President Clinton made it the very highest priority for his own staff and for all      
	911report/chapter-3.txt:            During 1995 and 1996, President Clinton devoted considerable time to seeking
	911report/chapter-3.txt:                President Clinton mentioned terrorism first in a list of several challenges facing     
	911report/chapter-3.txt:            In 1998, after Bin Ladin's fatwa and other alarms, President Clinton accepted a
	911report/chapter-3.txt:            This calculus becomes important in this story as both President Clinton and President      
	911report/chapter-3.txt:            President Bill Clinton's counterterrorism Presidential Decision Directives in 1995
	911report/chapter-3.txt:                Clinton made Tenet his informal personal representative to work with the Saudis on     
	911report/chapter-3.txt:                with President Clinton's blessing. Tenet reported that it was imperative to get an     
	911report/chapter-3.txt:            On August 7, 1998, National Security Advisor Berger woke President Clinton with a
	911report/chapter-3.txt:                strikes against the sites in Afghanistan. The Pentagon briefed President Clinton       
	911report/chapter-3.txt:                Shinrikyo's release of sarin nerve gas in the Tokyo subway. President Clinton
	911report/chapter-3.txt:            By the early hours of the morning of August 20, President Clinton and all his
	911report/chapter-3.txt:                and President Clinton flew back from his vacation on Martha's Vineyard to address      
	911report/chapter-3.txt:            At the time, President Clinton was embroiled in the Lewinsky scandal, which continued      
	911report/chapter-3.txt:                President Clinton, Vice President Gore, Berger, Tenet, and Clarke insisted to us       
	911report/chapter-3.txt:            Everyone involved in the decision had, of course, been aware of President Clinton's        
	911report/chapter-3.txt:                the Clinton administration had to reevaluate the threat posed by Bin RESPONSES TO AL   
	911report/chapter-3.txt:            In addition, the Clinton administration was facing the possibility of major combat
	911report/chapter-3.txt:                unfettered inspections could resume. The Clinton administration eventually launched    
	911report/chapter-3.txt:                1998. These military commitments became the context in which the Clinton
	911report/chapter-3.txt:                President Clinton and Berger also worried about the Economist's point-that attacks     
	911report/chapter-3.txt:                strikes. According to Clarke, President Clinton was inclined to launch further
	911report/chapter-3.txt:                Abdullah told President Clinton and Vice President Gore about this when he visited     
	911report/chapter-3.txt:            The State Department urged President Clinton to engage the Pakistanis. Accepting this      
	911report/chapter-3.txt:                advice, President Clinton invited Sharif to Washington, where they talked mostly       
	911report/chapter-3.txt:            Discussion within the Clinton administration on Afghanistan then concentrated on two       
	911report/chapter-3.txt:                Secretary Albright or First Lady Hillary Rodham Clinton-both critics of the
	911report/chapter-3.txt:                prevailed in July 1999, when President Clinton issued an executive order effectively   
	911report/chapter-3.txt:                the Taliban to stop sheltering Bin Ladin. President Clinton contacted Sharif again     
	911report/chapter-3.txt:                Washington thought this was likely to happen, President Clinton gave the idea his      
	911report/chapter-3.txt:                Kargil confrontation in Kashmir, President Clinton complained about Pakistan's
	911report/chapter-3.txt:            At first, the Clinton administration hoped that Musharraf 's coup might create an
	911report/chapter-3.txt:            As part of the response to the embassy bombings, President Clinton signed a
	911report/chapter-3.txt:                    by President William J. Clinton on December 4, 1998. Redacted material is
	911report/chapter-3.txt:            They finally agreed, as Berger reported to President Clinton, that an extraordinary        
	911report/chapter-3.txt:                sent a final draft to President Clinton, with an explanatory memo. The President       
	911report/chapter-3.txt:            Policymakers in the Clinton administration, including the President and his national       
	911report/chapter-3.txt:            In February 1999, another draft Memorandum of Notification went to President Clinton.      
	911report/chapter-3.txt:                Clinton crossed out key language he had approved in December and inserted more
	911report/chapter-3.txt:                this. President Clinton told the Commission that he had no recollection of why he      
	911report/chapter-3.txt:                their targets. After the August 20 strikes, President Clinton had had to call
	911report/chapter-3.txt:            President Clinton relied on the advice of General Shelton, who informed him that
	911report/chapter-3.txt:                was high. Shelton told President Clinton he would go forward with "boots on the        
	911report/chapter-3.txt:                intelligence. President Clinton told the Commission that "if we had had really good    
	911report/chapter-3.txt:                2001, the United States, and President Clinton personally, pressed the UAE, one of     
	911report/chapter-3.txt:            In February 1999, Tenet sought President Clinton's authorization to enlist Massoud
	911report/chapter-3.txt:            In July 1999, President Clinton authorized the CIA to work with several governments        
	911report/chapter-5.txt:                developed plans to assassinate President Clinton during his November 1994 trip to      
	911report/chapter-6.txt:                Tanzania, President Bill Clinton and his chief aides explored ways of getting Bin      
	911report/chapter-6.txt:                Ladin's organization remained intact. President Clinton was deeply concerned about     
	911report/chapter-6.txt:            In public, President Clinton spoke repeatedly about the threat of terrorism,
	911report/chapter-6.txt:                President Clinton during the crisis. He suggested threatening reprisals against the    
	911report/chapter-6.txt:            In mid-December, President Clinton signed a Memorandum of Notification (MON) giving        
	911report/chapter-6.txt:                naturalized U.S. citizen who, as Berger reminded President Clinton, had been in        
	911report/chapter-6.txt:            President Clinton was scheduled to travel to India. The State Department felt that he      
	911report/chapter-6.txt:                enough to merit a presidential visit. But President Clinton insisted on including      
	911report/chapter-6.txt:                there since 1969. At his meeting with Musharraf and others, President Clinton
	911report/chapter-6.txt:                proliferation, but also discussed Bin Ladin. President Clinton told us that when he    
	911report/chapter-6.txt:            The U.S. effort continued. Early in May, President Clinton urged Musharraf to carry        
	911report/chapter-6.txt:            In early March 2000, when President Clinton received an update on U.S.covert action        
	911report/chapter-6.txt:            At some point during this period, President Clinton expressed his frustration with
	911report/chapter-6.txt:                the statement, President Clinton recalled this remark as "one of the many things I     
	911report/chapter-6.txt:                assurance he will remain in place." President Clinton was kept up to date.
	911report/chapter-6.txt:                Clinton, Secretary Albright, and DCI Tenet all intervened to help. Because the
	911report/chapter-6.txt:            President Clinton told us that before he could launch further attacks on al Qaeda in       
	911report/chapter-6.txt:                Clinton administration, analysts stopped distributing written reports about who was    
	911report/chapter-6.txt:                next day, Berger and Clarke told President Clinton that while the investigation was    
	911report/chapter-6.txt:            On November 25, Berger and Clarke wrote President Clinton that although the FBI and        
	911report/chapter-6.txt:            In the same November 25 memo, Berger informed President Clinton about a closely held       
	911report/chapter-6.txt:            This, President Clinton and Berger told us, was not the conclusion they needed in
	911report/chapter-6.txt:                election and change of power was not the issue, President Clinton added. There was     
	911report/chapter-6.txt:                thought that, instead, President Clinton, Berger, and Secretary Albright were
	911report/chapter-6.txt:            No action was taken on these ideas in the few remaining weeks of the Clinton
	911report/chapter-6.txt:            As the Clinton administration drew to a close, Clarke and his staff developed a
	911report/chapter-6.txt:            In December, Bush met with Clinton for a two-hour, one-on-one discussion of national       
	911report/chapter-6.txt:                security and foreign policy challenges. Clinton recalled saying to Bush, "I think
	911report/chapter-6.txt:                Clinton told us that he also said,"One of the great regrets of my presidency is that   
	911report/chapter-6.txt:            Bush told the Commission that he felt sure President Clinton had mentioned terrorism,      
	911report/chapter-6.txt:                but did not remember much being said about al Qaeda. Bush recalled that Clinton had    
	911report/chapter-6.txt:            Their policy priorities differed from those of the Clinton administration. Those
	911report/chapter-6.txt:                Clinton administration had said specifically that Clarke's Counterterrorism Security   
	911report/chapter-6.txt:                formal than its predecessor's. President Clinton, a voracious reader, received his     
	911report/chapter-6.txt:                be a consequence." Since the Clinton administration had
	911report/chapter-6.txt:                the Clinton White House in November. This included the "preliminary judgment" that     
	911report/chapter-6.txt:                told about Clinton administration warnings to the Taliban. The President told us       
	911report/chapter-6.txt:                Clinton administration; he had no more success with Rice than he had with
	911report/chapter-6.txt:                Clinton administration documents. In fact, the CIA drafted two documents. One was a    
	911report/chapter-6.txt:                section would supersede the Clinton-era documents. Hadley wanted the authorities to  

This is useful to find all pertinent strings in a file in a certain folder.  

The last option I will be exploring is the -iname option. This option allows to find files with an approximate name.

Consider the following command.

	find 911report/ -iname "*chapter*1*"

 This command finds files with the words "chapter" and "1" in them.

Output:

	 911report/chapter-1.txt
	911report/chapter-10.txt
	911report/chapter-11.txt
	911report/chapter-12.txt
	911report/chapter-13.1.txt
	911report/chapter-13.2.txt
	911report/chapter-13.3.txt
	911report/chapter-13.4.txt
	911report/chapter-13.5.txt

 This is very useful to find files that you do not know the exact name of or to find files with similar naming conventions. 

 Consider this command:

	 find . -iname "*report*"

  It finds all the reports in the current directory.

  Output:

	  ./911report
	./government/About_LSC/commission_report.txt
	./government/About_LSC/Progress_report.txt
	./government/About_LSC/reporting_system.txt
	./government/About_LSC/Special_report_to_congress.txt
	./government/About_LSC/State_Planning_Report.txt
	./government/About_LSC/State_Planning_Special_Report.txt
	./government/About_LSC/Strategic_report.txt
	./government/Post_Rate_Comm/ReportToCongress2002WEB.txt

Again, this command finds all the files with the same naming convention (report) which is useful when all reports need to be read.
