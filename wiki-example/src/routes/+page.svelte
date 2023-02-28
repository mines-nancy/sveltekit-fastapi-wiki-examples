<html lang="fr">
    <h1>Exemples wiki SvelteKit</h1>
    <p>Toutes les explications se trouvent en commentaire dans le code</p>
    <h3>1.Exemple de formulaire basique</h3>
</html>

<script lang="ts">
  // Ici nous importons les composants acordéon et boutton de SMUI pour l'exemple N°2
  import Accordion, { Panel, Header, Content } from '@smui-extra/accordion';    //npm install --save-dev @smui-extra/accordion
  import Button from '@smui/button'                                             //npm install --save-dev @smui/button

  // Ici nous allons commencer par définir une variable pour chacun des champs du formulaire tel que :
  let name = '';
  let email = '';
  let message = '';
  let password = '';

  // Nous allons ensuite définir une fonction "handleSubmit" qui est appelée lorsque le formulaire est soumis. Cette fonction construit une chaîne de
  // texte à partir des variables "name", "email", "message" et "password" dont la valeur est récupérée grace à l'opérateur "$", et affiche cette chaîne
  // dans une boîte de dialogue à l'aide de "window.alert" :
  function handleSubmit() {
    const messageText = `Name: ${name}\nEmail: ${email}\nMessage: ${message}\nMot de passe: ${password}`;
    window.alert(messageText);
  }
  // Ici nous définissons une variable pour créer un compteur pour l'exemple N°2
  let counter = 0;
  // Ici nous définissons une fonction pour incrémenter le compteur dans l'exemple N°2
  function count(){
      counter++;
  }
</script>

<!--
Ensuite nous allons créé un formulaire qui appellera la fonction "handleSubmit" lorsque l'utilisateur soumet le formulaire.Nous utiliserons
ici la propriété "bind:value={nom_de_la_variable}" de svelte afin d'assigner les valeurs des input aux variables respectives que nous avons
définis précédemment :
-->
<html lang="fr">
    <form on:submit={handleSubmit}>
      <label>
        Nom :
        <input type="text" bind:value={name} />
      </label>

      <label>
        Email :
        <input type="email" bind:value={email} /> <!-- Un input de type email va automatiquement appliquer un regex -->
      </label>                                    <!-- pour vérifier s'il s'agit bien d'une adresse mail valide -->

      <label>
        Mot de passe :
        <input type="password" bind:value={password} /> <!-- Un input de type password va automatiquement cacher les -->
      </label>                                          <!-- caractère lorsque l'utilisateur écris -->

      <label>
        Message :
        <textarea bind:value={message}></textarea>
      </label>

      <button type="submit">Envoyer</button>
    </form>
</html>

<!--
Un peu de style pour pas que ça pique les yeux
-->

<style>
    html {
      font-family: 'Roboto';
    }

  form {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }

  label {
    display: flex;
    flex-direction: column;
    margin-bottom: 1rem;
  }

  input, textarea {
    resize:none;
  }
</style>

<html lang="fr">
    <h3>2.Exemple d'utilisation de SMUI</h3>
</html>

<div class="accordion-container">
<Accordion>                         <!-- Accordéon SMUI -->
    <Panel>                         <!-- Créer un nouveaux dépliable -->
        <Header>Exemple A : Texte</Header>  <!-- Titre -->
        <Content>                   <!-- Contenu : il est possible de mettre n'importe quoi dans un dépliable (image, texte, boutons etc...)-->
            Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
        </Content>
    </Panel>
    <Panel>
        <Header>Exemple B : Image</Header>
        <Content>
            <img src="/scarli.png" height="512" width="512"/>
        </Content>
    </Panel>
    <Panel>
        <Header>Exemple C : Bouton/Script</Header>
        <Content>
            Compteur : {counter}  <!-- On récupère la variable js "counter" grace aux opérateurs { }, ici pas besoins d'utiliser "$" car nous somme dans l'html et non le js -->
            <br>
            <Button variant="raised" on:click={count}>Incrémenter</Button> <!-- Le boutton SMUI appele la foncion "count" que nous avons définis précédemment dans le js -->
        </Content>
    </Panel>
</Accordion>
</div>
