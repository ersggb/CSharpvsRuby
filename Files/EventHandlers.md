### C# and Ruby Event Handler and Listeners Comparisons

  #### C#
  
  > C# allows for event handlers to signal the occorance of an action such as a button click.
  
  ```c#
  
  class Dog
  {
        public event EventHandler MaximumDerpReached;

        protected virtual void MaximumDerpReached(EventArgs e)
        {
            EventHandler handler = ThresholdReached;
            if (handler != null)
            {
                handler(this, e);
            }
        }
   }
  
  ```
  
  > Listeners are available to the Debug, Trace, and TraceSource classes, each of which can send its output to a variety of listener objects. The following are the commonly used predefined listeners:
  > * A TextWriterTraceListener redirects output to an instance of the TextWriter class or to anything that is a Stream class. It can also write to the console or to a file, because these are Stream classes.
  > * An EventLogTraceListener redirects output to an event log.
  > * A DefaultTraceListener emits Write and WriteLine messages to the OutputDebugString and to the Debugger.Log method. In Visual Studio, this causes the debugging messages to appear in the Output window. Fail and failed Assert messages also emit to the OutputDebugString Windows API and the Debugger.Log method, and also cause a message box to be displayed. This behavior is the default behavior for Debug and Trace messages, because DefaultTraceListener is automatically included in every Listeners collection and is the only listener automatically included.
  > * A ConsoleTraceListener directs tracing or debugging output to either the standard output or the standard error stream.
  > * A DelimitedListTraceListener directs tracing or debugging output to a text writer, such as a stream writer, or to a stream, such as a file stream. The trace output is in a delimited text format that uses the delimiter specified by the Delimiter property.
  > * An XmlWriterTraceListener directs tracing or debugging output as XML-encoded data to a TextWriter or to a Stream, such as a FileStream.
  
  ```c#
  
  System.Diagnostics.Trace.Listeners.Clear();  
  System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  

  
  ```
  
  #### Ruby
