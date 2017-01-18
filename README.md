
state AskBrainBot {
 pattern "ask brain bot" template askBrainBot();
 
 function askBrainBot() {
     // Get what the user said previously, and ask Brain Bot the question.
     var previous = conversation.input[-2].input;
     var message = new Object();
     message.message = previous;
     message.root = "chat";
     message.@instance = "165";
     message.@application = "yourappid";
     var result = Http.postXML("http://www.botlibre.com/rest/api/chat", message);
     if (result == null) {
         return "Brain Bot is not available";
     }
     return "He says: " + result.message;
 }
}
