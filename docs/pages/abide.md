---
title: Abide
description: Abide is an form validation library that extends the HTML5 validation API with custom validators.
sass: scss/forms/_error.scss
js: js/foundation.abide.js
tags:
  - forms
  - validation
---

### Abide Demo

These input types create a text field: `text`, `date`, `datetime`, `datetime-local`, `email`, `month`, `number`, `password`, `search`, `tel`, `time`, `url`, and `week`.

```html_example
<form data-abide novalidate>
  <div data-abide-error class="alert callout" style="display: none;">
    <p><i class="fi-alert"></i> There are some errors in your form.</p>
  </div>
  <div class="row">
    <div class="small-12 columns">
      <label>Number Required
        <input type="text" placeholder="1234" aria-describedby="exampleHelpText" required pattern="number">
        <span class="form-error">
          Yo, you had better fill this out, it's required.
        </span>
      </label>
      <p class="help-text" id="exampleHelpText">Here's how you use this input field!</p>
    </div>
    <div class="small-12 columns">
      <label>Nothing Required!
        <input type="text" placeholder="Use me, or don't" aria-describedby="exampleHelpTex" data-abide-ignore>
      </label>
      <p class="help-text" id="exampleHelpTex">This input is ignored by Abide using `data-abide-ignore`</p>
    </div>
    <div class="small-12 columns">
      <label>Password Required
        <input type="password" id="password" placeholder="yeti4preZ" aria-describedby="exampleHelpText" required >
        <span class="form-error">
          I'm required!
        </span>
      </label>
      <p class="help-text" id="exampleHelpText">Enter a password please.</p>
    </div>
    <div class="small-12 columns">
      <label>Re-enter Password
        <input type="password" placeholder="yeti4preZ" aria-describedby="exampleHelpText2" required pattern="alpha_numeric" data-equalto="password">
        <span class="form-error">
          Hey, passwords are supposed to match!
        </span>
      </label>
      <p class="help-text" id="exampleHelpText2">This field is using the `data-equalto="password"` attribute, causing it to match the password field above.</p>
    </div>
  </div>
  <div class="row">
    <div class="medium-6 columns">
      <label>URL Pattern, not required, but throws error if it doesn't match the Regular Expression for a valid URL.
        <input type="text" placeholder="http://foundation.zurb.com" pattern="url">
      </label>
    </div>
    <div class="medium-6 columns">
      <label>European Cars, Choose One, it can't be the blank option.
        <select id="select" required>
          <option value=""></option>
          <option value="volvo">Volvo</option>
          <option value="saab">Saab</option>
          <option value="mercedes">Mercedes</option>
          <option value="audi">Audi</option>
        </select>
      </label>
    </div>
  </div>
  <div class="row">
    <fieldset class="large-6 columns">
      <legend>Choose Your Favorite, and this is required, so you have to pick one.</legend>
      <input type="radio" name="pokemon" value="Red" id="pokemonRed"><label for="pokemonRed">Red</label>
      <input type="radio" name="pokemon" value="Blue" id="pokemonBlue" required><label for="pokemonBlue">Blue</label>
      <input type="radio" name="pokemon" value="Yellow" id="pokemonYellow"><label for="pokemonYellow">Yellow</label>
    </fieldset>
    <fieldset class="large-6 columns">
      <legend>Choose Your Favorite - not required, you can leave this one blank.</legend>
      <input type="radio" name="pockets" value="Red" id="pocketsRed"><label for="pocketsRed">Red</label>
      <input type="radio" name="pockets" value="Blue" id="pocketsBlue"><label for="pocketsBlue">Blue</label>
      <input type="radio" name="pockets" value="Yellow" id="pocketsYellow"><label for="pocketsYellow">Yellow</label>
    </fieldset>
    <fieldset class="large-6 columns">
      <legend>Check these out</legend>
      <input id="checkbox1" type="checkbox"><label for="checkbox1">Checkbox 1</label>
      <input id="checkbox2" type="checkbox" required><label for="checkbox2">Checkbox 2</label>
      <input id="checkbox3" type="checkbox"><label for="checkbox3">Checkbox 3</label>
    </fieldset>
  </div>
  <div class="row">
    <fieldset class="large-6 columns">
      <button class="button" type="submit" value="Submit">Submit</button>
    </fieldset>
    <fieldset class="large-6 columns">
      <button class="button" type="reset" value="Reset">Reset</button>
    </fieldset>
  </div>
</form>
```
---

<p>&nbsp;</p>

<div class="alert callout">
  <p><i class="fi-alert"></i> There are some errors in your form.</p>
</div>

<label class="is-invalid-label">
  Required Thing
  <input type="text" class="is-invalid-input">
  <span class="form-error is-visible">
    Yo, you had better fill this out.
  </span>
</label>

<label class="is-invalid-label">
  Required Thing
  <textarea type="text" class="is-invalid-input"></textarea>
</label>

## Initial State

```html
<form data-abide>
  <!-- Add "display: none" right away -->
  <div data-abide-error class="alert callout" style="display: none;">
    <p><i class="fi-alert"></i> There are some errors in your form.</p>
  </div>
  <label>
    Name
    <input type="text" required>
    <span class="form-error">This field is required.</span>
  </label>
</form>
```

## Error State

```html
<form data-abide>
  <!-- Add role="alert" -->
  <!-- Add "display: block" -->
  <div data-abide-error role="alert" class="alert callout" style="display: block;">
    <p><i class="fi-alert"></i> There are some errors in your form.</p>
  </div>
  <!-- Add "is-invalid-label" -->
  <label class="is-invalid-label">
    Name
    <!-- Add "is-invalid-input" -->
    <input type="text" class="is-invalid-input" required aria-invalid aria-describedby="uuid">
    <!-- Add "is-visible" -->
    <span class="form-error is-visible" id="uuid">This field is required.</span>
  </label>
</form>
```
