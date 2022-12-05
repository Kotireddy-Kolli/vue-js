
4 Ways to add vue
    1. CDN Package -> Adding script tag (Incorporate Vue to old legacy code base or quick prototype)
    2. nmp         -> npm install vue@next (prefered approch when bulding large scale app,
                        If you are familar with linters, formater, hot reloading, webpack configs, buld scripts )
    3. vue cli     -> npm install -g @vue/cli
                      vue create <project-name> 
                      cd <project-name>
                      npm run serve -> we can have app up and running(No need to config)
    4. vite        -> npm init vite-app <project-name>

.vue File
    HTML like syntax to describe a portion of the UI
    Contains 3 types of top-level language blocks(template,script,style)

Basic Terminology's
1.Binding Text
    a. Mustach Brackes {{}} or Text Interpollation
    b. Directive attribute(v-text="") -> Replace entire data of html element with the value -> Rerely used

2.Binding HTML
    We should only render the context you can trust, as it leads to cross site scripting attacks.
    It can open vulnerability's and threaths

3.Binding Attribute
    v-bind attribute

4.Binding Classs
    a. Static: we can just add in html element
    b. Dynamic: Where we need to add/remove classes based on senario/event ->
                We can use v-bind directive to bind javascript expression(&&,?) to the class attributes.
                Array-> we can pass all class names in array or onside array we can also conditinally add classes.
                Obj-> we can pass all class names in obj(key: value)pair.

5.Binding Styles
    For Styles, we can use v-bind, If property name is not single word we need to wrap in quotes('font-size') or Use camel case(fontSize)
                For numberic value we can append units( headersize+'px')

6.v-bind Shorthand
    No need to specify the v-bind, we can just use :attribute="value"

7.Conditional Redering
    v-if,
    v-if-else,
    v-else,
    v-show : Elememt will always be rendered but bases on expression result display property changes
    To render multiple elements -> we can use div or template as container

8.List render
    v-for="(name,index) from names" :key="index"->For Arrays
    v-for="(value,key,index) from names" :key="index" -> For Objects

9.Methods
    Any functions we should add inside the "methods" obj of vue
    We should not use arrow functions as vue binds this with data object, With arrow function that binding is lost.
    
10.Event
    v-on:eventToListen="code to execute" (or)
    @:eventToListen="code to execute"

    If no arg for methods, vue will pass the event obj as paramter,
    If the function has args, then you need to explecitly specify as $event

11.Forms
    v-model
    v-model.trim -> Modifiers

12.Computed property
    Are functions, When ever dependency chages, It will recalculate, No need to let vue know about dependency
    Why we need, When we can use declare funtion in methods property?
    Computed property's are cached, If we have some expensice calculations. If some thing independent
        of computed property change, The UI is rerendered. The cached result will be returned. This will improve the app performance.
    For sorting/filtering data

13.Computed Setter
    If you need to read/write the property

14.Watchers
    Allows you to watch any data or computed property and execute some code in response to change in the value.
    Define a funtion with same name of the variable that you wan to watch in watch object.
    By default watchers will receive 2 parameters(oldvalue , newvalue)
    immediate: true // Iy will load even on initial load.
    If you want to watch changes in an object/array(Deeply nested) // By default vue won't watch for changes. you need to give deep:true

15.Components
    a. Default export the Components
    b. import the component, specify the "props" property in script
    c. If we are passing multiple props, then in child you can define all the incomming prop in an array
    d. we can even define prop types, now declare props as an object(propname: Datatype)
    e. Dealing with number or boolean types, you need to pass those using v-bind:likes="50", otherwise we will got warning
    f. If any prop is mandetory, then convert the prop to object, Now specify
        title:{type:String, required:true}, If we don't received this prop, we will get warning.
        we can even set default value, default: 'article default title'

16.Non Prop Attribute
    We do have id, class, styles defined/passed for component.
    Those will be applied to single root element by default.
    If we need to apply to specific elements, then we can use v-bind attribute like, v-bind="$attrs"
    Also, specify "inheritAttrs:false" in script tag, to prevent default behavious of applying to single root.
    
17.Provide and Inject
    These 2 API's Provide a way for us to pass data thought the component tree without having to 
        pass down props manually at every level.
    We can define an new propery called "provide" object. Now go to component where you need the data
        specify the "inject" property array.

18.Custom Component Event
    If we want to communicate from child to parent.
    So, We can create a Custom event in child and emit that event(add property emit:['nameOfCustomeEvent(like close)']), 
        Inside the parent we listen to that custom event(@close="code to execute")
    We can also paas the data to parent along with event. we can pass data as second arg
        <button @click="$emit('close','Hi')">

19.Validating Custom Events
    In child before emiting the event lets validate the data that is being sent.
    Change the emit array to object, Key=custom event name and value is validation function.
    
20.Components & v-model
    Let's say we have multiple input in a form, and we want to create a component and reuse the component.
    If you add v-model to the component. The data binding wont happen(vue js dev tools), as v-model dont know 
        how to behave with custom component.
        a. If you are adding v-model to a component, it will automatically receive the prop "modelValue".
        Now, you can bind the value attr to modelValue.
        b. When we add v-model to component, It will automatically listen to the event "update:modelValue",
        All we have to do is tot emit the input value.

21.Slots
    a.Prop are great for component reusability, but we have parent-child relationship.
        Child will have the control of the HTML content, parent can only pass data values.
    b.Slots, 
        Allow re-usability of component, Allow parent component to control the content inside the child content.
        Allow parent to embed aby content in a child componentincluding html.

        Lets say we have card component, we pass text and it will be rendered in child. If we want image to recder?
        Component should have opening and closing tag, We can place any content in between. Go to child and place <slot></slot>
        The content from parent will replace the slot tags.

        Multiple slots? In parent specify them inside the template and give name "v-slot:name",
            In child specify the name prop for slot.