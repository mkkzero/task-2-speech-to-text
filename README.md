# this is the script for speech-to-text

// new speech recognition object
var SpeechRecognition = SpeechRecognition || webkitSpeechRecognition;
var recognition = new SpeechRecognition();
            
// This runs when the speech recognition service starts
recognition.onstart = function() {
    console.log("We are listening. Try speaking into the microphone.");
};

recognition.onspeechend = function() {
    // when user is done speaking
    recognition.stop();
}
              
// This runs when the speech recognition service returns result
recognition.onresult = function(event) {
    var transcript = event.results[0][0].transcript;
    var confidence = event.results[0][0].confidence;
};
              
// start recognition
recognition.start();

# this is the code

<!doctype html>
	<head>
		<style>
			/* CSS comes here */
			body {
			    font-family: arial;
			}
			button {
			    padding:10px;
			    background-color:#6a67ce;
			    color: #FFFFFF;
			    border: 0px;
			    cursor:pointer;
			    border-radius: 5px;
			}
			#output {
			    background-color:#F9F9F9;
			    padding:10px;
			    width: 100%;
			    margin-top:20px;
			    line-height:30px;
			}
			.hide {
			    display:none;
			}
			.show {
			    display:block;
			}
		</style>
		<title>JavaScript Speech to Text</title>
	</head>
	<body>
		<h2>JavaScript Speech to Text</h2>
        <p>Click on the below button and speak something...</p>
        <p><button type="button" onclick="runSpeechRecognition()">Speech to Text</button> &nbsp; <span id="action"></span></p>
        <div id="output" class="hide"></div>
		<script>
			/* JS comes here */
		    function runSpeechRecognition() {
		        // get output div reference
		        var output = document.getElementById("output");
		        // get action element reference
		        var action = document.getElementById("action");
                // new speech recognition object
                var SpeechRecognition = SpeechRecognition || webkitSpeechRecognition;
                var recognition = new SpeechRecognition();
            
                // This runs when the speech recognition service starts
                recognition.onstart = function() {
                    action.innerHTML = "<small>listening, please speak...</small>";
                };
                
                recognition.onspeechend = function() {
                    action.innerHTML = "<small>stopped listening, hope you are done...</small>";
                    recognition.stop();
                }
              
                // This runs when the speech recognition service returns result
                recognition.onresult = function(event) {
                    var transcript = event.results[0][0].transcript;
                    var confidence = event.results[0][0].confidence;
                    output.innerHTML = "<b>Text:</b> " + transcript + "<br/> <b>Confidence:</b> " + confidence*100+"%";
                    output.classList.remove("hide");
                };
              
                 // start recognition
                 recognition.start();
	        }
		</script>
	</body>
</html>


made by Mohanad Ghurab for the summer training for the IOT task in smart methods
