---
layout: default
title: "Formulaire de réponse"
weight: 3
---

### Formulaire de réponse

Merci de nous confirmer votre présence avant le 15 octobre, via le formulaire ci-dessous, ou par mail ou SMS (contact).

<form id="my-form" action="https://formspree.io/f/mnqllewr" method="POST">
  <label>Nom(s) et prénom(s):</label>
  <input type="text" name="Noms" />
  <br/>
  <input type="radio" id="coming" checked="true" name="Venue" value="Oui">
  <label for="coming">Avec plaisir !</label><br>
  <input type="radio" id="not-coming" name="Venue" value="Non">
  <label for="not-coming">Hélas, non…</label><br>  
  <button id="my-form-button">Envoyer</button>
  <p id="my-form-status"></p>
</form>



<style>
input[type=text] {
    height: 30px;
    margin-left: 10px;
    padding: 5px;
    min-width: 500px;
}
button {
    width: 100px;
    height: 30px;
    background: white;
    border: 1px solid gray;
}
button:hover {
   cursor: pointer;
}
@media only screen and (max-width: 800px) {
  input[type=text] {
      min-width: 90%;
  }
}
</style>

<script>
    var form = document.getElementById("my-form");
    
    async function handleSubmit(event) {
      event.preventDefault();
      var status = document.getElementById("my-form-status");
      var data = new FormData(event.target);
      fetch(event.target.action, {
        method: form.method,
        body: data,
        headers: {
            'Accept': 'application/json'
        }
      }).then(response => {
        status.innerHTML = "Merci de votre réponse !";
        form.reset()
      }).catch(error => {
        status.innerHTML = "Oups, nous n'avons pas pu envoyer votre réponse !"
      });
    }
    form.addEventListener("submit", handleSubmit)

</script>
