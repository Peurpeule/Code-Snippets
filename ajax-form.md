# Contact Form with Ajax


## HTML structure
* file : index.php 
```html
<form action="" method="post">
    <label for="email">Your email</label>
    <input type="email" id="email" placeholder="Your email">
    <div id="ajax-contact-response"></div>
    <input type="submit" value="Send" id="validate-contact">
 </form>
```

## Javascript event
* file : ajax-contact.js 
```javascript
$('#validate-contact').click(function (e) {
    e.preventDefault();
    /* Initialiser l'objet xhttp */
    var xhttp = new XMLHttpRequest();

    //Get email
    var mail = document.getElementById("email").value;

    //vérifier si XMLHttpRequest() est interprété par tous les navigateurs cf; activeXObject()...
    xhttp.onreadystatechange = function() {
        if (this.readyState == 4 && this.status == 200) {
            /* Display the result of PHP controller file in PHP view */
            document.getElementById("contact-response").innerHTML = this.responseText;
        }
    };
    /* Paramétrer le fichier de traitement php et lui passer des variables*/
    xhttp.open("GET", "traitement-formulaire-contact.php?mail="+mail, true);
    xhttp.send();
});
```
## PHP controller
* file : traitement-formulaire-contact.php 
```php
    if($_GET['mail'] != ''){
        if (filter_var($_GET['mail'], FILTER_VALIDATE_EMAIL)) {
            echo("Message sent successfuly");
            $to = "email@email.com"; // this is your Email address
            $from = $_GET['mail']; // this is the sender's Email address
            $name = $_GET['nom'];
            $subject = 'Message from ' . $_GET['prenom'] . ' ' . $_GET['nom'];
            $message = $name . " said :" . "\n\n" . $_GET['message'];
            $headers = "From:" . $from;
            mail($to,$subject,$message,$headers);
        }
        else {
            echo("Invalid email adress");
        }
    }
    else {
        echo("Email adress is required");
    }
```
