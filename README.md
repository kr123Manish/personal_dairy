## <a href="https://personal-dairy.netlify.app/">Overview</a>
#### Create a website which store our text info, for saving info we used <a href="https://firebase.google.com/docs/database">firebase</a>
<img src="https://github.com/kr123Manish/presonal_dairy/blob/main/1.jpg"></img>
<img src="https://github.com/kr123Manish/presonal_dairy/blob/main/2.jpg"></img>
<img src="https://github.com/kr123Manish/presonal_dairy/blob/main/3.jpg"></img>
### Note: This website is not 100% responsive, so please prefer laptop or pc for better experience. 
### <a href="https://personal-dairy.netlify.app/">Take demo..</a> 
### Prerequisite
- HTML-5
- CSS
- JavaScript
- <a href="https://firebase.google.com/docs/database/web/start">Basics of firbase realtime database.</a>
### Main Code
``` javascript
var firebaseConfig = {
   put your own config info
  };


    // Initialize Firebase
  firebase.initializeApp(firebaseConfig);
  var name,idno,note;
  // used to get all values from page for insert
  function ready(){
       name=document.getElementById("name").value;
       idno=document.getElementById("idno").value;
       note=document.getElementById("note").value;
      }


 // function for insert data.
  function insert(){
      ready();
         if(idno===''){
          alert("Mobile_no is required");
        }else{
         
          firebase.database().ref('Users/'+idno).set({
               Name: name,
               Idno: idno,
               Note: note
            });
          alert("Registered Successfully");
          display();
        }
  }

document.getElementById('insert').onclick=function() {
    const audio=new Audio();  // used for play audio when we click on button.
    audio.src="1.mp3";
    audio.play();
      insert();
    }

//for save notes
 function save_notes(){
            idno=document.getElementById('haveid').value;
            note=document.getElementById('note').value;
            var s=confirm("Save and Exit");
                     
            if(s==true){
                
                firebase.database().ref('Users/'+idno).update({
                    Note: note
                }); 

                    const audio=new Audio();
                    audio.src="1.mp3";
                    audio.play(); 
                   setTimeout(function () { location.reload(true); },1000);
                


            }

            else{
                firebase.database().ref('Users/'+idno).update({
                    Note: note
                });

                alert("Data is Saved");
              }
            
            
        
  }

document.getElementById('save').onclick=function() {
    const audio=new Audio();
    audio.src="1.mp3";
    audio.play();
    save_notes();
}
// for display data
  function display(){
        ready();
        idno = window.prompt("Enter Registered mob_no");
        if(idno===''){
          alert("mob_no is required");
        }else{
                firebase.database().ref('Users/'+idno).once('value',function(snapshot){
                  if(!snapshot.exists()){
                    alert(idno+" did not found");
                    document.getElementById('boss').style.display = 'block';
                  }else{
                        var havno=snapshot.val().Idno;
                        var n="Welcome: "+snapshot.val().Name;
                        var mn=n+" , Mob_no: " + havno;
                        document.getElementById("haveid").value=havno;
                        document.getElementById("info").value=mn;
                        document.getElementById("note").value=snapshot.val().Note;
                        userlogin(n);
                      }
                });


      }
  }

function userlogin(n){
    alert(n);
    document.getElementById('boss2').style.display = 'block';
  }
 
 // for update name

  function update(){
        ready();
        idno=window.prompt("Enter mob_no");
        name=window.prompt("Enter new name");

        // alert("Ready to update");
        if(idno===''){
          alert("mob_no is required");
        }
        else if(name===''){
          alert("name does not updated");
        }
        else{
            firebase.database().ref('Users/'+idno).update({
            Name: name
          });
      }
  }
  document.getElementById('update').onclick=function(){
    const audio=new Audio();
    audio.src="1.mp3";
    audio.play();
    update();
  }


// for delete data
  function del() {
        ready();
        idno=window.prompt("Confirm mob_no you want to delete");
        if(idno===''){
          alert("mob_no is required");
        }else{

            firebase.database().ref('Users/'+idno).once('value',function(snapshot){
                if(!snapshot.exists()){
                    alert(idno+" did not found");
                  }
                  else{
                    firebase.database().ref('Users/'+idno).remove();
                    alert(idno + " is removed");
                    location.reload();
                    }
                });
  }
}
  document.getElementById('delete').onclick=function(){
    const audio=new Audio();
    audio.src="1.mp3";
    audio.play();
    del();
  }



// for display call
//from home page
document.getElementById('login').onclick=function() {
    const audio=new Audio();
    audio.src="1.mp3";
    audio.play();
   document.getElementById('container').style.display = 'none';
    
    display();
}

//from register page
document.getElementById('display').onclick=function() {
    const audio=new Audio();
    audio.src="1.mp3";
    audio.play();
     document.getElementById('boss2').style.display = 'none';
     display();
}

//from textarea page
document.getElementById('display2').onclick=function() {
    const audio=new Audio();
    audio.src="1.mp3";
    audio.play();
    display();
}

//For call insert 
document.getElementById('signup').onclick=function() {
    // alert("Sign_up ready");
    const audio=new Audio();
    audio.src="1.mp3";
    audio.play();
    document.getElementById('container').style.display = 'none';
    document.getElementById('boss').style.display = 'block';
}

// for sound effect when hover the buttons.        
const audio2=new Audio();
audio2.src="2.mp3";
    
    document.getElementById("login").onmouseover=function() {
        audio2.play();
    }
    
    document.getElementById("signup").onmouseover=function() {
        audio2.play();
    }
     
    document.getElementById("display").onmouseover=function() {
        audio2.play();
    } 

    document.getElementById("insert").onmouseover=function() {
        audio2.play();
    } 

    document.getElementById("save").onmouseover=function() {
        audio2.play();
    } 

    document.getElementById("display2").onmouseover=function() {
        audio2.play();
    }

    document.getElementById("delete").onmouseover=function() {
        audio2.play();
    } 

    document.getElementById("update").onmouseover=function() {
        audio2.play();
    } 
  ```      
  ### <a href="https://personal-dairy.netlify.app/">Want to use..</a> 
  #### If you liked it don't forget to :star: it. 
