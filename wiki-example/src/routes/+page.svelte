<html lang="fr">
    <h1>Exemples wiki SvelteKit</h1>
    <p>Toutes les explications se trouvent en commentaire dans le code</p>
    <h3>1.Création d'un formulaire simple</h3>
</html>

<script>

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
    padding: 0.5rem;
    border: 1px solid #ccc;
    border-radius: 4px;
    resize:none;
  }

  button[type="submit"] {
    padding: 0.5rem 1rem;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }

  button[type="submit"]:hover {
    background-color: #0069d9;
  }

</style>