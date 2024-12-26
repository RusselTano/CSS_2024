# Theme sombre et clair

### SCSS

```scss
// Variables par défaut
$light-theme: (
  primary-color: #333,
  primary-background: #e4e4e4,
  highlight-color: hotpink,
  paint-background: #121212,
  paint-color: #fff
);

$dark-theme: (
  primary-color: #fafafa,
  primary-background: #121212,
  highlight-color: lime,
  paint-background: #fff,
  paint-color: #121212
);

// Mixin pour générer les styles basés sur un thème
@mixin theme($theme) {
  color: map-get($theme, primary-color);
  background-color: map-get($theme, primary-background);

  button {
    background-color: map-get($theme, highlight-color);
    color: map-get($theme, paint-color);
    border: none;
    padding: 10px 20px;
    cursor: pointer;
    border-radius: 5px;
    transition: background-color 0.3s ease, color 0.3s ease;

    &:hover {
      background-color: map-get($theme, paint-background);
      color: map-get($theme, highlight-color);
    }
  }
}

// Thème par défaut (clair)
:root {
  @include theme($light-theme);
}

// Thème sombre
.dark-theme {
  @include theme($dark-theme);
}

// Transition pour un changement fluide
body {
  transition: background-color 0.3s ease, color 0.3s ease;
}
```

### HTML

```html
<div>
  <button id="theme-switcher">Switch to Dark Theme</button>
</div>
```

### JavaScript

```javascript
// Récupérer le bouton
const themeSwitcher = document.getElementById('theme-switcher');

// Ajouter un gestionnaire d'événement pour basculer les thèmes
themeSwitcher.addEventListener('click', () => {
  document.documentElement.classList.toggle('dark-theme');

  // Mettre à jour le texte du bouton
  if (document.documentElement.classList.contains('dark-theme')) {
    themeSwitcher.textContent = 'Switch to Light Theme';
  } else {
    themeSwitcher.textContent = 'Switch to Dark Theme';
  }
});
```
