# DemoProject
Standalone demo project


import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashSet;
import java.util.List;
import java.util.Set;
/**
 * 
 * @author RamaKrishna
 *
 */
public class DeDup {

	public int[] randomIntegers = {1,2,34,34,25,1,45,3,26,85,4,34,86,25,43,2,1,10000,11,16,19,1,18,4,9,3,
           20,17,8,15,6,2,5,10,14,12,13,7,8,9,1,2,15,12,18,10,14,20,17,16,3,6,19,
           13,5,11,4,7,19,16,5,9,12,3,20,7,15,17,10,6,1,8,18,4,14,13,2,11};
	
	
	public static void main(String[] args) {
		
		DeDup obj = new DeDup();
		Integer[] output = obj.eliminateDuplicatesUsingArrayList();
		int[] result = DeDup.convertIntegerToPrimiteIntArray(output);
		
		System.out.println("Avoid duplicates using list output ");
		for(int k : result)
			System.out.print(k+",");
		System.out.println();
		
		Integer[] secondOutput = obj.eliminateDuplicatesUsingHashSet();
		int[] secondResult = DeDup.convertIntegerToPrimiteIntArray(secondOutput);
		
		System.out.println("Avoid duplicates using set output ");
		for(int k : secondResult)
			System.out.print(k+",");
		System.out.println();
		
		int[] thirdResult =obj.eliminateDuplicatesAfterSortingArray();
		System.out.println("Avoid duplicates after doing the sorting for the input array output ");
		for(int k : thirdResult)
			System.out.print(k+",");
		System.out.println();
		
		
	}
	
	/**
	 * This method will eliminate the duplicates from the int array using the hash set
	 * @return
	 */
	public Integer[] eliminateDuplicatesUsingHashSet(){
    	Set<Integer> hashSet = new HashSet<Integer>();
    	for(int i=0;i<randomIntegers.length;i++){
    		hashSet.add(randomIntegers[i]);
    	}  
    	return (Integer[])hashSet.toArray(new Integer[hashSet.size()]);
    }   
	
	/**
	 * This method will eliminate the duplicates from the int array using the ArrayList
	 * @return
	 */
	public Integer[] eliminateDuplicatesUsingArrayList(){
		List<Integer> output = new ArrayList<Integer>();
		for (int myValue : randomIntegers) {
		    if(!output.contains(myValue)){
				output.add(myValue);
			}	
		}		
		return (Integer[])output.toArray(new Integer[output.size()]);
	}

	/**
	 * This method will remove duplicates from the int arry after doing sort
	 * @return
	 */
	public int[] eliminateDuplicatesAfterSortingArray(){		
		Arrays.sort(randomIntegers);
        int a[] = randomIntegers;
		  int b=0;
		    a[b]=a[0];
		    for(int i=0;i<a.length;i++)
		    {
		        if (a[b]!=a[i])
		        {
		            b++;
		            a[b]=a[i];
		        }
		    }
		 int[] result = new int[b+1];
		 for(int k = 0; k <= b ; k++ ){
			 result[k] = a[k];
		 }
		return result;
	      
	}
	
	/**
	 * This method will construct the primitive int[] array from Integer[]
	 * @param arr
	 * @return
	 */
	public static int[] convertIntegerToPrimiteIntArray(Integer[] arr){		
		int[] result = new int[arr.length];
		for(int i=0; i < arr.length; i++ ){
			Integer b = arr[i];
			result[i] = b.intValue();
		}		
		return result;		
	}
}
