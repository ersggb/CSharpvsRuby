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

  > Ruby doesn't have specific listeners or event handlers, but it has a property called `Observable` which provides a simple mechanism for one object to inform a set of interested third-party objects when its state changes.
  
  ```ruby
  
  require "observer"

  class Ticker          ### Periodically fetch a stock price.
  include Observable

  def initialize(symbol)
    @symbol = symbol
  end

  def run
    last_price = nil
    loop do
      price = Price.fetch(@symbol)
      print "Current price: #{price}\n"
      if price != last_price
        changed                 # notify observers
        last_price = price
        notify_observers(Time.now, price)
      end
      sleep 1
    end
  end
end

class Price           ### A mock class to fetch a stock price (60 - 140).
  def self.fetch(symbol)
    60 + rand(80)
  end
end

class Warner          ### An abstract observer of Ticker objects.
  def initialize(ticker, limit)
    @limit = limit
    ticker.add_observer(self)
  end
end

class WarnLow < Warner
  def update(time, price)       # callback for observer
    if price < @limit
      print "--- #{time.to_s}: Price below #@limit: #{price}\n"
    end
  end
end

class WarnHigh < Warner
  def update(time, price)       # callback for observer
    if price > @limit
      print "+++ #{time.to_s}: Price above #@limit: #{price}\n"
    end
  end
end

ticker = Ticker.new("MSFT")
WarnLow.new(ticker, 80)
WarnHigh.new(ticker, 120)
ticker.run
  
  ```
