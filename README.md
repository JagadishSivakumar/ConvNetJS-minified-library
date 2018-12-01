# ConvNetJS-minified-library
ConvNetJS minified library, the source is from :https://cs.stanford.edu/people/karpathy/convnetjs/build/convnet-min.js

Link the minified file in the index file in your text-editor to get started instanatly:

Example code to get started:

    <html>
    <head>
      <title>Getting Started</title>
    <!--CSS goes here-->
    <style>
    body{
         background-color: red; /**Example**/
      }
     </style>
     
     <!--Importing the convetjs library-->
     <script src="minified.js">
     </script>
     
     <!--Javascript Content-->
     <script type="text/javascript">
     
    function periodic() {
    var d = document.getElementById('eg-divison');
    d.innerHTML = 'Random number: ' + Math.random()
    }
 
    var net; //global variable declared outside
    function start() {

      // this gets executed on startup
      //... 

      net = new convnetjs.Net();
      // ...

      // example of running something every 1 second
      setInterval(periodic, 1000);
    }


    </script>
    </head>

    <body onload="start()">
    <div id="eg-division"></div>
    </body>
    </html>     
    
