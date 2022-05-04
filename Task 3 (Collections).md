# (Collections)
------------

 **Saad Muhammad Saad** 
 

***Dr/Hanna Zeinedeen***

------------
# 1- Arraylist --  Non generic<br>
duplicated items <br>
any type
 

```csharp
 //  Arraylist >>Non generic
            ArrayList a = new ArrayList() { 1,2,3,4};
            a.Add(1);
            a.Add("saad");
            a.Add(true);
            int elemnt = (int)a[0];  //return 1 from indx 0
            a.AddRange( new ArrayList() { 88, 99, 77 });  //take a list inside or collection
            a.Insert(0,44); //must take an index 
            a.InsertRange(0, new ArrayList() { 44,55 }); //must take an index 
            a.Remove(44); //remove only the first 44 
            a.RemoveAt(0);  //index zero
            a.Remove("saad");
            a.Remove(true); 
            a.RemoveRange(0, 2);  //remove (two elemnts) [2>>Count]  from index 0 and 1
                                  // X a.Sort();  X cant used with different value types 
            Console.WriteLine(a.Contains(5)); //return true if it contains and false if not
            Console.WriteLine("----");
            int[] b = new int[8] ;
            /*CopyTo must take an array  */  a.CopyTo(1,b,4,3);  //copy from a from indx 1 to 3 to the array b start from idx 4 
            foreach (var x in a) Console.WriteLine(x);
            Console.WriteLine("----");
            foreach (var x in b) Console.WriteLine(x);

            Console.WriteLine("----");

            Console.WriteLine(a.IndexOf(3)); //Search specified element and returns index if found & Returns -1 if not
            Console.WriteLine("----");

            int[] c = (int[])a.ToArray(typeof(int)); //copy the whole elemnts of the arraylist a to an array b
            foreach (var x in c) Console.WriteLine(x);

            Console.WriteLine("----");
            ArrayList d = a.GetRange(1, 3); //return an array list from indx 1 with count 3 >> 3 numbers got
            foreach (var x in d) Console.WriteLine(x);

```
# 2- list  -- generic<br>
duplicated items <br>
one type only

   ```csharp
List<int> a = new List<int>() { 3,6,7,2,6}; 
            Console.WriteLine(  a.BinarySearch(6)); //return the idx of the number
            Console.WriteLine(a.BinarySearch(10)); //not found so return negative output
            
```
> The other important methods are the same as ArrayList



# 3- HashTable  -- Non generic<br>
- Hashtable stores key-value pairs<br>
- Keys must be unique and cannot be null<br>
- Values can be null or duplicate<br>
- sorted based on the key <br>

```csharp
Hashtable h = new Hashtable();
            h.Add("saad", 1);
            h.Add("mo", 2);
            h.Add("ahmed", 3);

            Console.WriteLine(  h.Contains("saad")); //search for the key >> return true or false
            Console.WriteLine(  h.ContainsKey("saad"));// the same as Contains
            Console.WriteLine(h.ContainsValue(2));//search for the values >> return true or false




            int[] newwVal = new int[10];
            h.Values.CopyTo(newwVal,1); //copy the valus of hashtable to the indx 1 of the array 

            foreach (var x in newwVal)
            {
                Console.Write(x + " ");
            }
            Console.WriteLine();
            string[] newwKeys = new string[10];
            h.Keys.CopyTo(newwKeys, 1); //copy the valus of hashtable to the indx 1 of the array 

            foreach (var x in newwKeys)
            {
                Console.Write(x+" "); //notice the spaces are NULL
            }
            Console.WriteLine();
            h.Remove("ahmed");
            foreach (DictionaryEntry x in h)//must write DictionaryEntry 
            {  
                Console.WriteLine(x.Key+" "+x.Value);
            }
            Console.WriteLine(h.Count); //the size of hashtable
```


# 4- Dictionary  -- generic<br>

•Keys must be unique and cannot be null.<br>

•Values can be null or duplicate

```csharp
Dictionary<string, int> d = new Dictionary<string, int>();
           d.Add("saad", 1);
           d.Add("mo", 2);
           d.Add("ahmed", 3);
           d.Add("mahmoud", 4);

           //dont include Contains() method like Hashtable
           Console.WriteLine(  d.ContainsKey("saad"));// the same as Contains
           Console.WriteLine(d.ContainsValue(2));//search for the values >> return true or false




           int[] newwVal = new int[10];
           d.Values.CopyTo(newwVal,1); //copy the valus of dic to the indx 1 of the array 

           foreach (var x in newwVal)
           {
               Console.Write(x + " ");
           }
           Console.WriteLine();
           string[] newwKeys = new string[10];
           d.Keys.CopyTo(newwKeys, 1); //copy the valus of dict to the indx 1 of the array 

           foreach (var x in newwKeys)
           {
               Console.Write(x+" "); //notice the spaces are NULL
           }
           Console.WriteLine();
           d.Remove("ahmed");
           foreach (KeyValuePair<string,int> x in d)//must write KeyValuePair< , > 
           {  
               Console.WriteLine(x.Key+" "+x.Value);
           }
           Console.WriteLine(d.Count); //the size of dict
           Console.WriteLine("-------");
           //to get the keys alone >> another way instead of CopyTo()

           Dictionary<string, int>.KeyCollection k =d.Keys;
           foreach (string s in k)
           {
               Console.Write(s+" ");
           }

           Console.WriteLine("------------");
           //to get the values alone >> another way instead of CopyTo()

           Dictionary<string, int>.ValueCollection v = d.Values;
           foreach (int x in v)
           {
               Console.Write(x + " ");
           }
``` 
# 5- Sorted List  -- Non generic<br>
- Such as Hashtable but sorted
- key must be the same type 
- values can be different types


```csharp
SortedList s = new SortedList();
            s.Add("saad", 2);
            s.Add("momo", 1);
            s.Add("ahmed", 3);

            Console.WriteLine( s.Contains("saad")); //search for the keys
            Console.WriteLine( s.Contains("fdf"));
            Console.WriteLine(s.ContainsKey("saad"));
            Console.WriteLine(s.ContainsKey("fwef"));

            Console.WriteLine(s.ContainsValue(3)); //search for values return true or false
            Console.WriteLine(s.ContainsValue(22));


            //to move the contents of the sorted ist must be put in a dictionary entry collection
            // string[] k = new string[10]; when using array of string 
            DictionaryEntry[] k = new DictionaryEntry[10];
            s.CopyTo(k, 2); 
            for (int i = 0; i < 10; i++)
            {
                Console.Write(k[i].Key+" "); 
            }
            Console.WriteLine("\n---------------");
           
            //store the values in a list also the same with keys
            IList list = s.GetValueList();
            for (int i = 0; i < s.Count; i++)
            {
                Console.Write(list[i]+" "); //print val
            }
            Console.WriteLine("\n---------------");

            IList list2 = s.GetKeyList();
            for (int i = 0; i < s.Count; i++)
            {
                Console.Write(list2[i] + " "); //print the key
            }
            Console.WriteLine("\n---------------");
            Console.WriteLine(s.IndexOfKey("saad")); //output the index 
            Console.WriteLine(s.IndexOfKey("efewfwef")); //output the index -1 coz it doesnt exist

            Console.WriteLine(s.IndexOfValue(2)); //output the index 
            Console.WriteLine(s.IndexOfValue(22)); //output the index -1 coz it doesnt exist

            s.Remove("saad"); //remove the key and its value
            s.RemoveAt(0);// delete the key and its value of indx 0


            //two ways of printing
            foreach (DictionaryEntry p in s)
            {
                Console.WriteLine(p.Key+" "+p.Value);
            }
            Console.WriteLine("---------");
            for (int i = 0; i < s.Count; i++)
            {
                Console.WriteLine(s.GetKey(i) + " " + s.GetByIndex(i)); //print the key and val
            }
```


# 6- Sorted List  -- generic<br>
- Such as Dictionary but sorted
- key must be the same type 
- values must be same type


```csharp
SortedList<string,int> s = new SortedList<string,int>();
           s.Add("saad", 2);
           s.Add("momo", 1);
           s.Add("ahmed", 3);
           s.Add("mahmoud", 4);
           s.Add("abdo",6);

           Console.WriteLine(s.ContainsKey("saad"));
           Console.WriteLine(s.ContainsKey("fwef"));

           Console.WriteLine(s.ContainsValue(3)); //search for values return true or false
           Console.WriteLine(s.ContainsValue(22));
        //  ❌❌ s.CopyTo(k, 2);  // No copyto() Method
       
           // ❌❌ s no getvaluelist
         //  IList list = s.GetValueList();
         
           Console.WriteLine(s.IndexOfKey("saad")); //output the index 
           Console.WriteLine(s.IndexOfKey("efewfwef")); //output the index -1 coz it doesnt exist

           Console.WriteLine(s.IndexOfValue(2)); //output the index 
           Console.WriteLine(s.IndexOfValue(22)); //output the index -1 coz it doesnt exist

           s.Remove("saad"); //remove the key and its value
           s.RemoveAt(0);// delete the key and its value of indx 0

           Console.WriteLine("========");
           int x ;//such as an indicator for true o false
           Console.WriteLine(s.TryGetValue("m76omo",out x));  //m76omo is not exist 
           Console.WriteLine(x);

           Console.WriteLine(s.TryGetValue("momo",out x));  //momo is exist 
           Console.WriteLine(x);
           Console.WriteLine("========");
           //two ways of printing
           foreach (var p in s)
           {
               Console.WriteLine(p.Key+" "+p.Value);
           }
           Console.WriteLine("---------");
           for (int i = 0; i < s.Count; i++)
           {
               Console.WriteLine(s.Keys[i] + " " + s.Values[i]); //print the key and val
           }
```
# 7- Stack --Non generic<br>
- last-in, first out LIFO collection 
of object.
```csharp
Stack st = new Stack();
         st.Push("saad");  
         st.Push("momo");
         st.Push("ahmed");
         st.Push("mahmoud");
```
+----------+---+
| Top 
+==========+===+
| mahmoud >> fourth
+----------+---+
| ahmed >> third
+----------+---+
| momo >> sec
+----------+---+
| saad >> added first
+----------+---+

 ```csharp
Console.WriteLine(st.Peek());  //the output >> mahmoud
```

```csharp
Stack st = new Stack();

            st.Push("saad");
            st.Push("momo");
            st.Push("ahmed");
            st.Push("mahmoud");
            Console.WriteLine(st.Count);
            Console.WriteLine(st.Peek());

            Console.WriteLine(st.Contains("sa")); // false not founded
            Console.WriteLine(st.Contains("saad")); // true founded

            Console.WriteLine(st.Pop());


            Stack st2 = new Stack();
            st2.Push(6);
            st2.Push(8);
            st2.Push(9);
            st2.Push(11);
            int[] arr = new int[6];
            st2.CopyTo(arr, 2); //one-dimensional Array that copied from stack.
            for (int i = 0; i < 6; i++) Console.Write(arr[i] +" ");


            Console.WriteLine("\n++++++++++++++");
          object []arr2= st2.ToArray();
            for (int i = 0; i < 4; i++)
            {
                Console.Write(arr2[i] + " ");
            }
            Console.WriteLine("\n another way");
            foreach (var it in arr2) //var or Object
            {
                Console.Write(it+" ");
            }
            Console.WriteLine("\n++++++++++++++");


           
            foreach(var it in st){
                Console.Write(it+ " ");
            }
```
# 8- Stack -- generic<br>
- last-in, first out LIFO collection 
of object.

```csharp
Stack<string> st = new Stack<string>();

           st.Push("saad");
           st.Push("momo");
           st.Push("ahmed");
           st.Push("mahmoud");
           Console.WriteLine(st.Count);
           Console.WriteLine(st.Peek());

           Console.WriteLine(st.Contains("sa")); // false not founded
           Console.WriteLine(st.Contains("saad")); // true founded
           string x = "no thing in the stack";
         //  Console.WriteLine(st.TryPeek(out x));
           //Console.WriteLine(st.Pop());
         
           Console.WriteLine("trypeek>> "+ st.TryPeek(out x)); //output is true   coz he is on the peak
           Console.WriteLine(x);          //so x will store the peak 
           st.Clear();
           Console.WriteLine("trypeek>> " + st.TryPeek(out x));   //output false   now stack is empty so no peak
           Console.WriteLine(x);                                   //so x will be the defalut value of its type which is null

           Stack<int> st2 = new Stack<int>();
           st2.Push(6);
           st2.Push(8);
           st2.Push(9);
           st2.Push(11);
           int[] arr = new int[6];
           st2.CopyTo(arr, 2); //one-dimensional Array that copied from stack.
           for (int i = 0; i < 6; i++) Console.Write(arr[i] +" ");


           Console.WriteLine("\n++++++++++++++");
         int []arr2= st2.ToArray();    //we deleted Object and write int 
           for (int i = 0; i < 4; i++)
           {
               Console.Write(arr2[i] + " ");
           }
           Console.WriteLine("\n another way");
           foreach (var it in arr2) //var or Object
           {
               Console.Write(it+" ");
           }
           Console.WriteLine("\n++++++++++++++");


          
           foreach(var it in st){
               Console.Write(it+ " ");
           }
```
# 9- Queue -- Non generic<br>
- It represents a first-in, first out collection of object (FIFO)

- When you add an item in the list it goes at the back such a line 

```csharp
Queue q = new Queue();
           q.Enqueue("saad"); //the push is to the back
           q.Enqueue("momo");
           q.Enqueue("mahmoud");
           q.Enqueue("ahmed");
           
           string[] arr = new string[10];
           q.CopyTo(arr, 2);  //copy the q elements to the ar string from indx two 
                                   // the indx 0 & 1 are NULL
           foreach (var item in arr) // var or Object
           {
               Console.Write(item + " ");
           }
           q.Dequeue();  //remove from the front
           Console.WriteLine("\nthe peek >> "+q.Peek());
           Console.WriteLine(q.Contains("saad")); //return true or false
           foreach(var item in q) // var or Object
           {
               Console.Write(item +" ");
           }
           Console.WriteLine("--------------------");
           Queue qq = new Queue();
           qq.Enqueue(2); //the push is to the back
           qq.Enqueue(4);
           qq.Enqueue(5);
           qq.Enqueue(8);
           Object[] arr2=qq.ToArray(); // Returns Object[] so u cant replace Object with int  coz its non generic
           foreach (var item in arr2) // var or Object
           {
               Console.Write(item + " ");
           }
           Console.WriteLine("\nsize = "+qq.Count);
```
# 10- Queue -- generic<br>
- It represents a first-in, first out collection of object (FIFO)

- When you add an item in the list it goes at the back such a line 

```csharp
Queue <string>q = new Queue<string>();
           q.Enqueue("saad"); //the push is to the back
           q.Enqueue("momo");
           q.Enqueue("mahmoud");
           q.Enqueue("ahmed");

           string[] arr = new string[10];

           q.CopyTo(arr, 2);  //copy the q elements to the ar string from indx two 
                                   // the indx 0 & 1 are NULL

           foreach (var item in arr) // var or Object
           {
               Console.Write(item + " ");
           }
           q.Dequeue();  //remove from the front
           Console.WriteLine("\nthe peek >> "+q.Peek());
           Console.WriteLine(q.Contains("saad")); //return true or false
           foreach(var item in q) // var or Object
           {
               Console.Write(item +" ");
           }


           Console.WriteLine("--------------------");

           Queue<int> qq = new Queue<int>();
           qq.Enqueue(2); //the push is to the back
           qq.Enqueue(4);
           qq.Enqueue(5);
           qq.Enqueue(8);

           int[] arr2=qq.ToArray(); // Returns the same type initialized[] u can replace Object with int 
         
           foreach (var item in arr2) // var or Object
           {
               Console.Write(item + " ");
           }
           int x = 10;
           Console.WriteLine("\n"+qq.TryPeek(out x));
           Console.WriteLine("x= "+x); //if there is a peak  so x = the peak 
           qq.Clear();  //cleared so no peak
           Console.WriteLine("\n" + qq.TryPeek(out x));
           Console.WriteLine("x= " + x); // there is no peak  so x = default value of int which is 0 
           Console.WriteLine("\nsize = "+qq.Count);
```
