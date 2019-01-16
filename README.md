# Editable Resume with HTM (Hyperscript Tagged Markup)

An easily and interactively editable resume form. This project is developed using the [htm](https://github.com/developit/htm) project which is **amazing**! HTM uses JSX-like syntax and it is possible to develop with react/preact directly within a html file. It is very useful for the small integration of preact in large projects.

With a single html file and with some ajax calls of course, existing cv data is loaded and updated data is uploaded. Editing the resume is super easy and fast thanks to p/react's *component-based* and lightweight structure.

> See the [live demo](https://editable-resume.mucahit.me/).



## Usage
Several type of interactions for editing have been designed.

 - *For the text blocks* **double click** should be used to edit and pressing **enter** or clicking out of the focus area should enough to save new data.
 - *For the list items*, with minus button, existing list items might be deleted or with plus button, new items might be selected on a dropdown and added to the list.
 - *For the multiple text blocks* double click is used to edit existing blocks. Plus button is used to add new block and minus is used to remove an existing block.
 - *For the list items with sliders*, it is like list items however, slider is used to select a percent over %100. Just double click on the list item and click on the slider for the selecting percentage.

## Integration
Importing HTM module;  

    ```javascript
    <script  type="module">
    // import HTM
    import  {  html,  Component,  render  }  from  'https://unpkg.com/htm/preact/standalone.mjs';
    ...
    ```
Import existing data in `ComponentDidMount()` . An ajax call to backend might be useful to get existing data, and with `setState` function data can be stored in the state.

    ```javascript
    this.setState({
	    cv:{
		    nameSurname:  'Mucahit Gurbuz',
		    jobTitle:  'Civil Engineer',
		    contactEmail:  'contact@mucahit.me',
		    contactTelephone:  '05352017608',
		    contactWebsite:  'mucahit.me',
		    contactAddress:  'Ankara, Turkey',
		    interestAreas:  ['Software',  'Ground Improvement',  'Pavement'],
		    birthDate:  '27.04.1993',
		    age:  '22-24',
		    ...
		}
	})
    ```
Design the form according to your requests. Just use the blocks  

    ```javascript
    <${EditableText}
	    placeholder="Website"
	    name="contactWebsite"
	    isEditable=${isEditable?isEditable.contactWebsite:false}
	    toggleIsEditableCB=${this.toggleIsEditable}
	    value=${cv?cv.contactWebsite:''}
	    valueUpdater=${this.updateTextInput}
	    onBlurSave=${this.onBlurSave}
	>
	    <label>${cv?cv.contactWebsite:''}</label>
    </${EditableText}>
    ```
Just change the `contactWebsite` to another parameter.
To submit updated data to backend use `onSubmit` function;  

    ```javascript
    onSubmit(){
	    console.log(this.state.cv);
	    // In here the updated cv data can be send to backend using ajax calls.
	}
    ```
The data inside the state is always the updated. Therefore, it may use to send cv data to anywhere anytime.


