
1. Create a function (work for the thread)
2. Create a thread
3. Start the thread
4. Maybe... join it back into the main thread

```C#
void function() {/* work */} // create a function for the thread

Thread t = new Thread(function); // inserts a delegate
t.Start(); // start the thread
// Here your main thread can do shit
// This is where parallelization works
t.Join(); // Wait for it to finish (optional)
```

- `t.Start()` is *non-blocking*
	- It returns right away, allowing the main thread to continue immediately
- `t.Join()` is *blocking*
	- Caller thread waits until `t` is finished
		- `t` is finished when the worker function returns
	- Use this to properly order your thread operations

## Arguments
How do we add arguments if we must have a `void` function signature?

> We use [[Closures|closures]], we wrap our worker function in an object with fields

### Example

```C#
public Class AddWorker
{
	public int start;
	public int end;
	public long sum = 0; // our sum is too big for int
	public int[] arr; // personal array
	
	public void DoWork()
	{
		for(int i = start; i < end; i++)
			sum += arr[i];
	}	
}

public class Program
{
	static void Main(stringp[] args)
	{
		int[] nums = Sequence(10000000);
		
		// Should output 50000005000000 (i think)
		
		// 1. Need some work to do
		AddWorker w1 = new AddWorker();
		w1.start = 0;
		w1.end = nums.Length / 2;
		w1.arr = nums;
		
		AddWorker w2 = new AddWorker();
		w2.start = nums.Length / 2;
		w2.end = nums.Length;
		w2.arr = nums;
		
		// 2. Create threads to do the work
		Thread t1 = new Thread(w1.DoWork);
		Thread t2 = new Thread(w2.DoWork);
		
		// 3. Start Threads
		t1.Start();
		t2.Start();
		
		// 4. Wait for threads to finish
		// If we don't join, then we just print what the threads
		// currently have summed up.
		t1.Join();
		t2.Join();
		
		// 5. Print Results
		Console.WriteLine(w1.Sum + w2.Sum);
	}
}
```