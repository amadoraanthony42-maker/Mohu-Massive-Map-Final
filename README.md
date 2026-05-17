# Mohu-Massive-Map-Final
var idList = getColumn("dogs", "id");
var nameList = getColumn("dogs", "dog name");
var countryList = getColumn("dogs", "country");
var descList = getColumn("dogs", "short description ");
var imageList = getColumn("dogs", "image");
var socialsList= getColumn("dogs", "social media");

playSound("mycasa(tritonhacksmix)--AudioTrimmer.com--(1).mp3", true);

var saveList = [];
var currentPin;

var currWorld = 1;
var worldAmt = 8;
 
for(var i = 1; i <= worldAmt; i++){
  onEvent("right"+i, "click", function( ) {
    if(currWorld<worldAmt){
      currWorld++;
    } else {
      currWorld = 1;
    }
    setScreen("world"+currWorld);
  });
  onEvent("left"+i, "click", function( ) {
    if(currWorld>1){
      currWorld--;
    } else {
      currWorld = worldAmt;
    }
    setScreen("world"+currWorld);
  });
  
  onEvent("Save"+i, "click", function() {
    if(isAdded()>=0){
      removeItem(saveList, isAdded());
        setProperty("Save" + currWorld, "image", "icon://fa-bookmark-o");
    } else {
      appendItem(saveList, currentPin);
      setProperty("Save" + currWorld, "image", "icon://fa-bookmark");
    }
    console.log(saveList);
  });
  onEvent("Next"+i, "click", function(){
    setScreen("SaveScreen");
    for(var b = 0; b < saveList.length; b++){
      var currElement = "SaveNamedtext"+(b+1);
      showElement(currElement);
      setProperty(currElement, "text", nameList[saveList[b]]);
      
      currElement="SaveCountryText"+(b+1);
      
      showElement(currElement);
      setProperty(currElement, "text", countryList[saveList[b]]);
    }
  });
  
}
 onEvent("startButton", "click", function( ) {
   setScreen("world1");
   
 });
 
onEvent("world1", "click", function(){
  hideElement("tutorialImage");
  hideElement("tutorialText");
});

onEvent("returnButton", "click", function(){
  setScreen("world"+currWorld);
});



for(var k = 1; k <=1; k++){
  onEvent("Pin"+k, "click", function(){
    currentPin = 0;
    showPopup();
    setInfo(0);
    
  });
}
for(k; k<=3; k++){
  onEvent("Pin"+k, "click", function(){
    currentPin = 1;
    showPopup();
    setInfo(1);
    
  });
}
for(k; k<=5; k++){
  onEvent("Pin"+k, "click", function(){
    currentPin = 2;
    showPopup();
    setInfo(2);
    
  });
}
for(k; k<=7; k++){
  onEvent("Pin"+k, "click", function(){
    currentPin = 3;
    showPopup();
    setInfo(3);
    
  });
}
for(k; k<=8; k++){
  onEvent("Pin"+k, "click", function(){
    currentPin = 4;
    showPopup();
    setInfo(4);
    
  });
}
for(k; k<=9; k++){
  onEvent("Pin"+k, "click", function(){
    currentPin = 5;
    showPopup();
    setInfo(5);
    
  });
}
for(k; k<=11; k++){
  onEvent("Pin"+k, "click", function(){
    currentPin = 6;
    showPopup();
    setInfo(6);
    
  });
}
for(k; k<=13; k++){
  onEvent("Pin"+k, "click", function(){
    currentPin = 7;
    showPopup();
    setInfo(7);

  });
}
for(k; k<=14; k++){
  onEvent("Pin"+k, "click", function(){
    currentPin = 8;
    showPopup();
    setInfo(8);
  });
}
for(k; k<=17; k++){
  onEvent("Pin"+k, "click", function(){
    currentPin = 9;
    showPopup();
    setInfo(9);
  });
}
for(k; k<=19; k++){
  onEvent("Pin"+k, "click", function(){
    currentPin = 10;
    showPopup();
    setInfo(10);
    
  });
}
for(k; k<=23; k++){
  onEvent("Pin"+k, "click", function(){
    currentPin = 11;
    showPopup();
    setInfo(11);
    
  });
}





function showPopup() {
  if(isAdded()>=0){
    setProperty("Save" + currWorld, "image", "icon://fa-bookmark");
  } else {
    setProperty("Save" + currWorld, "image", "icon://fa-bookmark-o");
  }
  
  showElement("Name" + currWorld);
  showElement("PopupImage" + currWorld);
  showElement("Close" + currWorld);
  showElement("DescriptionText" + currWorld);
  showElement("Dredbackground" + currWorld);
  showElement("infoText" + currWorld);
  showElement("Save" + currWorld);
 
  

}
function hidePopup() {
  hideElement("Name" + currWorld);
  hideElement("PopupImage" + currWorld);
  hideElement("Close" + currWorld);
  hideElement("DescriptionText" + currWorld);
  hideElement("Dredbackground" + currWorld);
  hideElement("infoText" + currWorld);
  hideElement("Save" + currWorld);
}

//returns -1 if is not added, if is added, returns a the index of the number that is added
function isAdded(){
  var result = -1;
  for(var p = 0; p<saveList.length; p++){
    if(saveList[p]==currentPin){
      result = p;
    }
  }
  
  return result;
}



function setInfo(who) {
  setProperty("Name" + currWorld, "text", "Hi! My name is " + nameList[who]);
  setProperty("DescriptionText" + currWorld, "text", descList[who]);
  setProperty("PopupImage" + currWorld, "image", imageList[who]);
  setProperty("infoText" + currWorld, "text", "From:" + "\n" + countryList[who] + "\n\n" + socialsList[who]);
}
for(var g = 1; g <= 8; g++){
  onEvent("Close"+g, "click", function(){
    hidePopup();
  });
}

onEvent("HomeButton", "click", function( ) {
  setScreen("start");
});

