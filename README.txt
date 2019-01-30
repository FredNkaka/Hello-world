/*
Activity: Contact manager
*/

// TODO: Complete the program

var Contact = {
  init: function(firstName, lastName){
    this.firstName = firstName;
    this.lastName = lastName;
  },
  options: function(){
    var contactoptions = "1: List contact \n 2: Add a contact \n 0: Quit \n";
    return contactoptions;
  }
};
console.log("Welcome to your contacts manager!");
console.log(Contact.options());
var contact1 = Object.create(Contact);
contact1.init("John", "Smith");

var contact2 = Object.create(Contact);
contact2.init("Jane", "Doe");

var contacts = [];
contacts.push(contact1);
contacts.push(contact2);

//Create a function to print out the contacts
function listContacts(contactsArray){
  for (var i= 0; i < contactsArray.length; i++){
    console.log("Last name: " + contactsArray[i].lastName + ", first name: " + contactsArray[i].firstName);
  }
}

console.log("Here's a list of your contacts: ");
listContacts(contacts);

//Deal with user selected option
var userOption = prompt("Choose an option 2 to contin...: ");
if( userOption == 1 || userOption == 2 || userOption == 0){
  while(userOption == 1 || userOption == 2 || userOption == 0){
    if(userOption == 1){
      //display the contacts
      console.log("Here's a list of your contacts: ");
      listContacts(contacts);
      break;
    } else if (userOption == 2){
      //add a new contact
      var newContact = Object.create(Contact);
      var newFirstName = prompt("Please enter the first name: ");

      if(newFirstName == 0 ){
        //quit
        break;
      } else if(newFirstName != 0){
        var newLastName = prompt("Please enter the last name: ");
        if(newLastName == 0){
          //quit
          break;
        } else {
          //Add the new contact to the contacts
          newContact.init(newFirstName, newLastName);
          contacts.push(newContact);
          console.log("Contact added");
          listContacts(contacts);
          console.log("Press 0 to quit.");
        }
      }
    } else if (userOption == 0){
      //quit
      break;
    }
  }
} else {
  //Incase of wrong input from the user
  console.log("Please enter a valid option from the options.");
}

