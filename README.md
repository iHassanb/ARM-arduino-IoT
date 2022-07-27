# ARM-arduino-IoT

## Java Script
In the code below, I invoked the Web Speech Recognition API and initialized an instance stored in  recognition variable.
After this, I made references to  #textbox and #instructions components I characterized in the HTML utilizing JQuery to control them from the code.
content variable keeps track of text the application has converted and displayed in the textarea from the HTML file.
recognition.lang='ar'; for arabic language.

ex Git :
```
var speechRecognition = window.webkitSpeechRecognition
var recognition = new speechRecognition()
var textbox = $("#textbox")
var instructions = $("#instructions")
var content = ''
recognition.continuous = true
recognition.lang ='ar';
recognition.onstart = function() {
 instructions.text("ابدأ التحدث")
}
```
The onstart event handler is triggered when the recognition API starts and has microphone access.

ex Git :
```
recognition.onstart = function() {
 instructions.text("ابدأ التحدث")
}
```
onresult event handler is triggered when the recognition API has successfully converted speech from the user’s microphone to text, and the data is made available via the event.results variable.

ex Git :
```
recognition.onresult = function(event) {
 var current = event.resultIndex;
 var transcript = event.results[current][0].transcript
 content += transcript
 textbox.val(content)
}
```
Now If click the اضغط للبدء button your speech will convert to text
### Arduino.js
Filter on devices with the Arduino USB vendor ID.

ex Git :
```
 filters: [{ usbVendorId: 0x2341 }],
        };
```
 Request an Arduino from the user.
 
 ex Git :
 ```
  port = await navigator.serial.requestPort(requestOptions);
        await port.open({ baudRate: 115200 });
        writer = port.writable.getWriter();
        isConnectted = true;
      } catch (e) {
        console.log("err", e);
      }
    }
  ```
