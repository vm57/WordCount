import java.util.*;
import java.io.*;

public class Main
{
	public static void main(String[] args) 
	{
	    String fileName="text.txt";
	    Main m=new Main();
	    Set<String> s=m.wordSeprate(fileName);
	    Map<String,Integer> map=m.wordCount(s,fileName);
	    for(Map.Entry mm:map.entrySet())
	    {
	        System.out.println("The word "+mm.getKey()+" comes in "+mm.getValue()+" times");
	    }
	}
	
	public Set wordSeprate(String fileName)
	{
	    Set<String> wordSet=new HashSet<String>();
	    try(FileReader fr=new FileReader(fileName);
	    BufferedReader br=new BufferedReader(fr);)
	    {
    	    String line="";
    	    while((line=br.readLine())!=null)
    	    {
    	        String arr[]=line.split(" ");
    	        for(String word : arr)
    	        {
    	            wordSet.add(word.toLowerCase());
    	        }
	        }
	    }
	    catch(Exception e)
	    {
	        System.out.println(e.getMessage());
	    }
	    return wordSet;
	}
	
	public Map wordCount(Set s,String fileName)
	{
	    Map<String,Integer> map=new HashMap<String,Integer>();
	    Set<String> set=s;
	    try(FileReader fr=new FileReader(fileName);
	    BufferedReader br=new BufferedReader(fr);)
	    {
    	    String line="";
    	    for(String str :set)
    	    {
    	        int count=0;
        	    while((line=br.readLine())!=null)
        	    {
        	        String arr[]=line.split(" ");
        	        for(String word : arr)
        	        {
        	            if(set.equals(word.toLowerCase()))
        	            count++;
        	        }
    	        }
    	        map.put(str,count);
    	    }
    	    return map;
	    }
	    catch(Exception e)
	    {
	        System.out.println(e.getMessage());
	    }
	    return map;
	}
}
