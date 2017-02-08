
import java.util.Arrays;
import java.util.Scanner;
public class TorchBridge 
{
 
    /* Function takes the number of people crossing and the time taken by each
     * Assuming that boat can take 2 people */
    public static int TotalTime(int[] mem, int n) {
    	if (n == 3) 
    	{
            return mem[0] + mem[1] + mem[2]; 
    	}
        else if (n < 3) 
        {
            return mem[n-1];
        } 
        else 
        {
            int t1 = mem[n-2]+mem[0]+mem[n-1]+mem[0];
            int t2 = mem[1]+mem[0]+mem[n-1]+mem[1];
             
            if (t1 < t2)
            {
                return  t1 + TotalTime(mem, n - 2);
            }
            else if (t2 < t1)
            {
                return  t2 + TotalTime(mem, n - 2); 
            }
            else
            {
                return  t2 + TotalTime(mem, n - 2); 
            }
        }
    }
 
    public static void main(String[] args) {
        System.out.println("Enter the number of people crossing:");         
        Scanner input = new Scanner(System.in);
        int n = input.nextInt();
        int[] mem = new int[n];
        System.out.println("Enter the time taken by each person");
        while(input.hasNextInt())
        {
        	for(int member = 0; member < n ; member++)
        	{
        		mem[member] = input.nextInt();
        	}
        }
        Arrays.sort(mem);
        System.out.println("The total time take to cross the bridge is: ");
        System.out.println(TorchBridge.TotalTime(mem, n));
           
    }
 
}
