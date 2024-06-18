# JAVASRIPT-Debugging

- Event listeners are objects or callback functions <br>
- Causes of memory leaks <br>
  * Adding an event listener but not removing the DOM object
  * Adding variables to the global object
  * Setting objects as data on a DOM element ---> Uses more memory than available
    
#### Developer Tools that can help you debug memory issues

###### There are a few different tools available in the Memory Inspector:
  * Heap Snapshot - how memory is distributed among JavaScript objects - what is taking up the memory
  * Allocation Instrumentation on time line - memory allocations over time - identify where objects are and why aren’t they garbage collected hence remain in memory. 
  * Allocation sampling - memory allocations using a sampling method - Record snapshots for long-running operations and using stack trace to identify where allocations are

###### The Heap Snapshot tab has 4 different views:

Summary view: groups objects by constructor 
Comparison view: displays the difference between Heap snapshots. if you use more memory or garbage collection.
Containment view: analyzes objects referenced in the global (Window) object and not being garbage collected.
Statistics view: how memory is being used for Code, Strings, and JS arrays.




Chrome Dev Tools: How to use the Memory Inspector
Part 1: Open DevTools to allocate and inspect memory
  * Console tab where function is logged shows characters and memory taken. 
Part 2: With the Memory tab find JavaScript objects and amount of memory they take using heap snapshot - find memory leaks
   * Memory tab 1st shows the 3 tools Heap Snapshot, Allocation Instrumentation, Allocation Sampling
     * Select Heap Snapshot
     * Take a snapshot which creates a profile
         * Select profile gives a drop down to Heap different views - Summary, Containment, Statistics
         * Summary view - Groups the objects instances based on the class Constructor function used to instantiate the object. (can search by class)
         * Click the class constructor to view the instance objects properties
         * The constructor that created the instance is found in __prototype__ -> constructor
               * Hovering will provide a link this help track the origin of the instance and can take you to the source and which line the function is on.
               * Shallow size is how much memory all the instance created by constructor is using
               * Various heap shots can show if this amount is increasing over time.
               * more instances created will take up more memory
Part 3: Guided Debugging of a Memory Issue
Part 4: Use the Performance Tab to measure memory usage over time 
  * how you can analyze the runtime performance of your applications and locate a potential performance bottleneck.
      * See in red in the time line is a sign of an issue
  * Warning message you can find from a lab:
                 - Forced reflow is a likely performance bottleneck
                    - A browser has to recalculate the size and location of elements on your page - called a layout. 
                    - Fix by adjusting styles or layouts models like flexbox  
                 - Long task took 
                 - Handler took
    
Adding variables to the global scope is one of the many issues that can cause memory leaks
Global scope variables can’t be garbage collected.

ou can use Chrome DevTools to identify performance issues, memory leaks, and other memory issues when analyzing and testing your code.

With tools like heap snapshots and the performance timeline, you can dig into a ton of details about your code’s memory allocation and performance.

This can help you answer questions like where memory was allocated from down to the line of code, why a piece of memory isn’t being garbage collected, how memory is growing over time, and more.
