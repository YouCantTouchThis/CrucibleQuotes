'strict mode';



var http = require('http');




exports.handler = function(event, context) {
    try {
        // Good to initalize attributes
         var request = event.request;
         var session = event.session;
        if(!event.session.attributes) {
          event.session.attributes = {};
        }
        

         if (request.type === "LaunchRequest") {
           handleLaunchRequest(context);
    
         } else if (request.type === "IntentRequest") {
           if (request.intent.name === "HelloIntent") {
             handleHelloIntent(request, context);
           } else if(request.intent.name === "QuoteIntent") {
             handleQuoteIntent(request,context,session);
           } else if(request.intent.name === "NextQuoteIntent") {
             handleNextQuoteIntent(request, context, session);
           } else if(request.intent.name === "AMAZON.HelpIntent") {
             let options = {};
             options.speechText = "Hey guardian, who would you like a quote by? Just say the character's name.";
             options.endSession = false;
             context.succeed(buildResponse(options));
           } else if(request.intent.name === "AMAZON.FallbackIntent") {
             let options = {};
             options.speechText = "Oh no looks like something went wrong, try again by saying a character name";
             options.endSession = false;
             context.succeed(buildResponse(options));
           } else if(request.intent.name === "AMAZON.StopIntent" || request.intent.name === "AMAZON.CancelIntent") {
             context.succeed(buildResponse({
               speechText: "Good bye guardian." + "<break time=\".1s\"/> May the light be with you.",
               endSession: true
             }));
           }  else {
              throw "Unknown Intent";
           }
    
          } else if (request.type === "SessionEndedRequest") {
    
          } else {
             throw "Unknown intent type";
          }
           
       } catch(e) {
         context.fail("Excpetion: " + e);
       }
};



function buildResponse(options) {
  var response = {
    version: 1.0,
    response: {
      outputSpeech: {
        type: "SSML",
        ssml: "<speak>" + options.speechText + "</speak>"
      },
      shouldEndSession: options.endSession
    }
  };

  if(options.repromptText) {
    response.response.reprompt = {
      outputSpeech: {
        type: "SSML",
        ssml: "<speak>" + options.repromptText + "</speak>"
      }
    };
  }
  
  if(options.session && options.session.attributes) {
    response.sessionAttributes = options.session.attributes;
  }
  
  return response;
  
}

function handleLaunchRequest(context) {
  let options = {};
           options.speechText = "Welcome Guardian <break time=\".08s\"/>, who would you like to hear a quote by?";
           options.repromptText = " You can say for example, shaxx ";
           options.endSession = false;
           context.succeed(buildResponse(options));
}

var shaxx_lib = [ 
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/lxnonBu5-stand-tall-guardian-this-battle-is-lost-but-their-will-be-others+(1).mp3\"/>",
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/jd1RAcCC-guardians-are-measured-by-their-ability-to-come-back-from-defeat-so-stand-fight+(1).mp3\"/>", 
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/idzplXpH-you-have-the-fortitude-and-persistance-of-lord-salidin-you-can-tell-him-i-said-that+(1).mp3\"/>",
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/OMsDcbcE-fight-like-a-demon-for-these-zones-bring-your-friends-i-need-more-like-you+(1).mp3\"/>",
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/LVKANDtb-what-where-s-my-catharsis-boo-boooo+(1).mp3\"/>",
      "<audio src=\"https://caydedialogues.s3.us-east-2.amazonaws.com/are+you+trying+to+kill+me%2C+just+win.mp3\"/>",
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/seventh+column+(1).mp3\"/>",
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/you+can+fight+by+my+side+any+time+guardian+(1).mp3\"/>",
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/YEEEEEEEESS+(1).mp3\"/>",
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/you+may+be+defeated+but+you+must+never+surrender+(1)+(1).mp3\"/>",
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/was+that+all+of+them+that+was+all+of+them+(1).mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/are+you+trying+to+play+me+arcite+take+my+sword+im+going+in+there.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/did+no+one+tell+you+two+monsters+that+crimson+days+are+a+holiday+celebration+you+beat+the+taste+out+of+them+now+do+it+again.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/friendship+is+a+blunt+instrument+use+it+to+crush+your+enemies.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/go+make+them+cry.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/listen+if+anyone+ever+asks+you+two+who+brought+you+together+you+tell+them+it+was+me.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/some+people+think+i+dont+like+hunters+i+dont+i+love+them.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/welcome+to+crimson+days+where+we+cherish+our+partners+and+annihilate+the+opposition.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/you+two+remind+me+of+lady+efrideet+and+myself+she+was+my+partner+once+she+likes+to+throw+titans+and+some+titans+like+to+be+thrown.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/you+two+remind+me+of+lord+saladin+and+myself+he+was+my+partner+once+no+one+can+best+his+fist+of+havoc+except+me.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/your+opponent+is+single+now+finish+this.mp3\"/>"
      ];
var cayde_lib = [
  "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/Cayde+6+intuitive+(1).mp3\"/>",
  "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/Cayde+Audio1+(1).mp3\"/>",
  "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/am_i_right+(1).mp3\"/>",
  "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/cayde_6+(1).mp3\"/>",
  "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/cayde_6_radiochatter+(1).mp3\"/>",
  "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/cayde_6_ramen_time+(1).mp3\"/>",
  "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/cayde_here_we_go+(1).mp3\"/>",
  "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/cayde_orders_a_pie+(1).mp3\"/>",
  "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/cayde_quote+(1).mp3\"/>",
  "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/destiny_regicide+(1).mp3\"/>",
  "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/gun_i_borrow+(1).mp3\"/>",
  "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/hugs+(1)+(1).mp3\"/>",
  "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/i+gotta+go+see+about+a+ship.mp3\"/>",
  "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/miss+the+little+guy.mp3\"/>",
  "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/told+you+my+stealth+drive+would+work.mp3\"/>"
  ];
  
  var saladin_lib = [
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/a+glorious+dawn+is+coming+guardian+finish+this.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/a+guardian+fights+for+as+long+as+they+intend+to+find+me+again+when+you+are+ready.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/a+powerful+statement.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/a+whole+fireteam+gone+just+like+that.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/all+of+you+together+like+iron+lords.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/and+thats+how+you+gain+ground.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/cayde-6+would+be+proud.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/defeat+is+not+the+end+be+defiant+guardian+fight+again.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/defeat+only+stops+you+if+you+let+it+the+iron+banner+is+always+open+to+you.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/die+die+di...+ahem+sorry+I+have+uh+i+have+been+watching+too+many+iron+banner+matches+what+time+is+it+shaxx+shaxx+are+you+there+can+you+get+me+a+water+stop+yelling+its+just+a+question+im+not+old.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/do+they+fear+you+they+should.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/do+you+like+it+better+when+lord+shaxx+oversees+these+matches+so+do+i+a+busy+shaxx+is+a+quiet+shaxx.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/does+ikora+know+you+are+this+good+ill+tell+her+i+havent+talked+to+her+in+a+while.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/dont+let+up+until+they+are+dust+guardian+this+isnt+over.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/enemy+has+closed+the+gap+hammer+a+new+one.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/even+light+can+fade.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/every+guardian+loses+the+key+is+what+you+do+next+fight+again.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/first+blood+is+yours+theyll+fight+harder+now.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/good+counter+now+hit+them+again.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/guardian+crush+them.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/i+havent+met+a+warrior+like+you+since+the+dark+age+guardians+are+saints+so+polite+i+think+the+city+makes+them+that+way+its+easy+to+be+an+angel+in+heaven+but+you+understand+youre+no+saint.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/i+keep+telling+cayde-6+to+watch+your+feed+he+needs+to+see+what+it+means+to+be+effective+that+exo+is+a+mess.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/i+wish+the+iron+lords+could+have+met+you+they+wouldve+hated+you+youd+push+them+to+be+better.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/in+the+dark+age+we+called+this+fun.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/lord+shaxx+couldnt+have+done+it+better.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/shaxx+must+envy+your+strength.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/shaxx+would+be+yelling.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/so+much+glory+so+little+time.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/sometimes+the+greatest+revenge+is+to+simply+persist+finish+them.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/there+are+days+when+even+when+the+vanguard+get+sloppy+but+not+like+you+you+have+iron+focus.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/this+isnt+over+until+shaxx+sings+and+he+is+very+shy.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/titans+the+iron+lords+had+those+we+called+them+big+people.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/warlocks+the+iron+lords+had+those+we+called+them+smart+people.mp3\"/>",
  "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/youre+the+one+zavala+talks+about.mp3\"/>"
  ];
  
  var big_lib = [
    "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/lxnonBu5-stand-tall-guardian-this-battle-is-lost-but-their-will-be-others+(1).mp3\"/>",
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/jd1RAcCC-guardians-are-measured-by-their-ability-to-come-back-from-defeat-so-stand-fight+(1).mp3\"/>", 
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/idzplXpH-you-have-the-fortitude-and-persistance-of-lord-salidin-you-can-tell-him-i-said-that+(1).mp3\"/>",
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/OMsDcbcE-fight-like-a-demon-for-these-zones-bring-your-friends-i-need-more-like-you+(1).mp3\"/>",
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/LVKANDtb-what-where-s-my-catharsis-boo-boooo+(1).mp3\"/>",
      "<audio src=\"https://caydedialogues.s3.us-east-2.amazonaws.com/are+you+trying+to+kill+me%2C+just+win.mp3\"/>",
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/seventh+column+(1).mp3\"/>",
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/you+can+fight+by+my+side+any+time+guardian+(1).mp3\"/>",
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/YEEEEEEEESS+(1).mp3\"/>",
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/you+may+be+defeated+but+you+must+never+surrender+(1)+(1).mp3\"/>",
      "<audio src=\"https://shaxxquotes.s3.us-east-2.amazonaws.com/was+that+all+of+them+that+was+all+of+them+(1).mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/are+you+trying+to+play+me+arcite+take+my+sword+im+going+in+there.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/did+no+one+tell+you+two+monsters+that+crimson+days+are+a+holiday+celebration+you+beat+the+taste+out+of+them+now+do+it+again.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/friendship+is+a+blunt+instrument+use+it+to+crush+your+enemies.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/go+make+them+cry.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/listen+if+anyone+ever+asks+you+two+who+brought+you+together+you+tell+them+it+was+me.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/some+people+think+i+dont+like+hunters+i+dont+i+love+them.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/welcome+to+crimson+days+where+we+cherish+our+partners+and+annihilate+the+opposition.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/you+two+remind+me+of+lady+efrideet+and+myself+she+was+my+partner+once+she+likes+to+throw+titans+and+some+titans+like+to+be+thrown.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/you+two+remind+me+of+lord+saladin+and+myself+he+was+my+partner+once+no+one+can+best+his+fist+of+havoc+except+me.mp3\"/>",
      "<audio src=\"https://shaxxquotesnew.s3.us-east-2.amazonaws.com/your+opponent+is+single+now+finish+this.mp3\"/>",
      "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/Cayde+6+intuitive+(1).mp3\"/>",
      "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/Cayde+Audio1+(1).mp3\"/>",
      "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/am_i_right+(1).mp3\"/>",
      "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/cayde_6+(1).mp3\"/>",
      "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/cayde_6_radiochatter+(1).mp3\"/>",
      "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/cayde_6_ramen_time+(1).mp3\"/>",
      "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/cayde_here_we_go+(1).mp3\"/>",
      "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/cayde_orders_a_pie+(1).mp3\"/>",
      "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/cayde_quote+(1).mp3\"/>",
      "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/destiny_regicide+(1).mp3\"/>",
      "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/gun_i_borrow+(1).mp3\"/>",
      "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/hugs+(1)+(1).mp3\"/>",
      "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/i+gotta+go+see+about+a+ship.mp3\"/>",
      "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/miss+the+little+guy.mp3\"/>",
      "<audio src=\"https://caydequotesonlycayde.s3.us-east-2.amazonaws.com/told+you+my+stealth+drive+would+work.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/a+glorious+dawn+is+coming+guardian+finish+this.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/a+guardian+fights+for+as+long+as+they+intend+to+find+me+again+when+you+are+ready.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/a+powerful+statement.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/a+whole+fireteam+gone+just+like+that.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/all+of+you+together+like+iron+lords.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/and+thats+how+you+gain+ground.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/cayde-6+would+be+proud.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/defeat+is+not+the+end+be+defiant+guardian+fight+again.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/defeat+only+stops+you+if+you+let+it+the+iron+banner+is+always+open+to+you.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/die+die+di...+ahem+sorry+I+have+uh+i+have+been+watching+too+many+iron+banner+matches+what+time+is+it+shaxx+shaxx+are+you+there+can+you+get+me+a+water+stop+yelling+its+just+a+question+im+not+old.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/do+they+fear+you+they+should.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/do+you+like+it+better+when+lord+shaxx+oversees+these+matches+so+do+i+a+busy+shaxx+is+a+quiet+shaxx.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/does+ikora+know+you+are+this+good+ill+tell+her+i+havent+talked+to+her+in+a+while.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/dont+let+up+until+they+are+dust+guardian+this+isnt+over.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/enemy+has+closed+the+gap+hammer+a+new+one.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/even+light+can+fade.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/every+guardian+loses+the+key+is+what+you+do+next+fight+again.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/first+blood+is+yours+theyll+fight+harder+now.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/good+counter+now+hit+them+again.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/guardian+crush+them.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/i+havent+met+a+warrior+like+you+since+the+dark+age+guardians+are+saints+so+polite+i+think+the+city+makes+them+that+way+its+easy+to+be+an+angel+in+heaven+but+you+understand+youre+no+saint.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/i+keep+telling+cayde-6+to+watch+your+feed+he+needs+to+see+what+it+means+to+be+effective+that+exo+is+a+mess.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/i+wish+the+iron+lords+could+have+met+you+they+wouldve+hated+you+youd+push+them+to+be+better.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/in+the+dark+age+we+called+this+fun.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/lord+shaxx+couldnt+have+done+it+better.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/shaxx+must+envy+your+strength.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/shaxx+would+be+yelling.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/so+much+glory+so+little+time.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/sometimes+the+greatest+revenge+is+to+simply+persist+finish+them.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/there+are+days+when+even+when+the+vanguard+get+sloppy+but+not+like+you+you+have+iron+focus.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/this+isnt+over+until+shaxx+sings+and+he+is+very+shy.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/titans+the+iron+lords+had+those+we+called+them+big+people.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/warlocks+the+iron+lords+had+those+we+called+them+smart+people.mp3\"/>",
      "<audio src=\"https://saladinquotes.s3.us-east-2.amazonaws.com/youre+the+one+zavala+talks+about.mp3\"/>"
      
      
  ];
  
    function randomQuotes(arr){  
      var factIndex = Math.floor(Math.random() * arr.length);
      var randomQuote = arr[factIndex];
      return randomQuote;
    }


var lib = big_lib;
function handleHelloIntent(request, context) {
  let options = {};
  var name = request.intent.slots.name.value; 
  if(name.indexOf("shaxx") != -1 || name.indexOf("shacks") != -1  ) {
    lib = shaxx_lib;
    options.speechText = randomQuotes(lib);
    options.speechText += "Do you want to listen to one more quote from shaxx?" ;
    options.endSession = false;
    context.succeed(buildResponse(options));
  } else if (name.indexOf("cayde") != -1) {
    lib = cayde_lib;
    options.speechText = randomQuotes(lib);
    options.speechText += "Do you want to listen to one more quote from cayde? ";
    options.endSession = false;
    context.succeed(buildResponse(options));
  } else if (name.indexOf("saladin") != -1) {
    lib = saladin_lib;
    options.speechText = randomQuotes(lib);
    options.speechText += "Do you want to listen to one more quote from saladin? ";
    options.endSession = false;
    context.succeed(buildResponse(options)); 
  } else if (name.indexOf("quote") != -1)  {
    lib = big_lib;
    options.speechText = randomQuotes(lib);
    options.speechText += "Do you want to listen to one more random quote?";
    options.endSession = false;
    context.succeed(buildResponse(options)); 
  } else if (name.indexOf("ikora") != -1 || name.indexOf("zavala") != -1 || name.indexOf("eververse") != -1 || name.indexOf("hawthorne") != -1 || name.indexOf("bot") != -1 || name.indexOf("calus") != -1)  {
    options.speechText = "Looks like we don't support that character. Try again.";
    options.endSession = true;
    context.succeed(buildResponse(options)); 
  }  else {
    options.speechText = "Oh no looks like something went wrong<break time=\".1s\"/>, restart the skill by asking alexa to open it again.";
    options.endSession = true;
    context.succeed(buildResponse(options));
  }
            options.speechText = randomQuotes(lib);
                options.speechText += "Do you want to listen to another quote?";
                options.endSession = false;
                context.succeed(buildResponse(options));
              }


function handleQuoteIntent(request,context,session) {
  let options = {};
  options.session = session;
                options.speechText = randomQuotes(lib);
                options.speechText += "Do you want to listen to one more quote?";
                options.repromptText = "You can say yes <break time=\".1s\"/> or one more.";
                options.session.attributes.quoteIntent= true;
                options.endSession = false;
                context.succeed(buildResponse(options));
              }
function handleNextQuoteIntent(request, context, session) {
  let options = {};
  options.session = session;
                options.speechText = randomQuotes(lib);
                options.speechText += "Would you like another quote?";
                options.repromptText = "You can say yes <break time=\".1s\"/> or one more.";
                session.attributes.quoteIntent= true;
                options.endSession = false;
                context.succeed(buildResponse(options));
              
              }
            
