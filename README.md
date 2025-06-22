who create
  - angular => Google
  - react => facebook
  - vue => even you from google

angular is framework
  - because it is collection from libararys and has it design pattern

angular is component base
angular is single page application

babel => convert ES6 to old javascript

data validation VS format validation
  - birth data 5/6/2028
    - correct format validation
    - inccorrect data validation


single page application vs multiple page application
  - multiple page application (SSR)
    -- it is best at SEO
    -- it is fast at initail reload
    -- it is bad at relaod when navigate at pages => because it send request every time
  - single page application (CSR)
    -- it switch component in index.html
    -- it is bad at SEO
    -- it is not fast at initail reload => because it loading all things
    -- it has not relaod when navigate at pages 


folder structure
  - .angular => it created when do run project, it is cashing for project
  - tscongif.json => it include configration about typescript
  - tscongif.app.json => it include configration about typescript for app file
  - package.json => all packages and libaray for our project
  - package-lock.json => more details about packages and depandances packages
  - angular.json => we import libararys at this file (css | js) and translation
  
@.. => directive


// importants
- ng new myproject => to create project angular
- npm g c ComponentName ==> to create componenet
- npm g i InterfaceName ==> to create interface
- npm g d DirectiveName ==> to create directive
- npm i @rxweb/reactive-form-validators => libarary for validation
- npm i jwt-decode => to do decode for token
- ng g c componenet/navbar
- ng g g util/guards/auth
- ng g interceptor nameInterceptor
- npm i ngx-toastr => to display message by style
- npm i ngx-spinner => to create sppiner loading

- npm i @ngx-translate/core => to install services and pipes for translate
- npm i @ngx-translate/http-loader => to install loading files for translate

- ctrl + shift + alt + v => to transfer object to interface


-npm i @fortawesome/fontawesome-free => then restart server

- when use image from assets change path to "./assets/imageUlr" because in run time the folder assets will be neer by index.html 


============= week1 ================
1-binding
    i- one way data binding
        - data interpolation {{}} => to write innertext in tages , we can use it with property but it do not work with condition
        - property binding []
        - attribute binding [attr.]
        - event binging ()
        - class binding
        - style binding
    ii- two way data binding
        -- ngMode => at input



2- control flow vs directive
    i- control flow 
          - for if switch
          - built in angular
          - added after version 16
          - it best in preformance => becauase track
          - it has empty function
          - @for
            - $index => return boolean value
            - $count => return boolean value
            - $first => return boolean value
            - $last => return boolean value
            - $even => return boolean value
            - $odd => return boolean value
            - track => to do render for specific element only without do for loop again => it improve the preformance

          - @if, @else => to show and hide element
              - it remove element from dom
          
          - @switch
    
    ii- directive 
        - ng-for => ngFor="let product of products"
        - ng-if
        - ng-switch
        - we do import from angler  
        - it write in tag html
        - can not we use index directive , we must store index in 
        - it is not best in preformance => becauase it has not track but can create track
        - it has not empty function
        - we can not use two directive in the same tag => but can use <ng-container> to use more one directive in the same tag ,  it do not create element in html 
        - <ng-template #referance> => it not appeare if you call it by referance
    
3- lazyloading for sepecific part in page
    i- by using @defer(){sepecific part} (CSR)
        - it is not good for SEO => the psepecific part inside @defer not reder at server (SSR)
        - it is good for preformance
        - it has two parameter (on,when)
            -- on => default = idle
                --- time(3s) => it will show section after 3 seconds
                --- interaction(#elementReferance) => it will show section after click on button or keydown on input
                --- hover(#elementReferance) => it will show section after hover another element
                --- viewport(#elementReferance) => it will show section when scroll to element
            -- when + condition(user == "admin")
            -- we can use them together as OR by using ';' between them
    ii- @placeholder(minimum 5s) => it render at server SSR, (minimum 5s)=> option
        - it appeare before data loading
    iii- @loading(minimum 5s){} it render at client CSR,  (minimum 5s)=> option
        - it appeare durring data loading
    iv- @error{} it render at client CSR
        - if occur error in defer

4- @ViewChild(elementReferance) => to select frist element from file.html, include nativeElement
4- @ViewChild(selector-componenet) => to select frist componenet from file.html to access the varibles and methids in child componenet
4- ViewChildren(elementReferance) => to select elements from file.html => do loop by forEach


5- content projection => we put design html between  selctor componenet tag 
    - <app-alert>design html</app-alert>
    - to send design html from parent to child
    - we use '<ng-content/>' to put the content in child => it has attribute select to select sepesific tag

6- @input (dicorator) => it used for transfer data from parent to chiled

7- @output => 
    - we use it to create custom event to send data from child to parent => @Output itemEvent:EventEmitter = new EventEmitter() , fairEvent(){ this.itemEven.emit(data)} => we call it when click on button at child
    - recive data at $event at child selector = > <app-chiled (itemEvent)="getData($event)"></app-chiled> 

8- withInMemoryScrolling({scrollPositionRestoration:""}) at file app.config.ts => to solve scroll page problem (to star scroll from top)
    - disable => defualt when scroll between page, page started scroll from last scroll in last page
    - top => return scroll to top when transfer between page and effect on forward and backward
    - enable => return scroll to top when transfer between page, but not effect on forward and backward

9- withHashLocation =>it put '#' at url  (file app.config.ts)
    - to solve relative path at server


10- custom Directive => we used it if have the same properties at the element and we want to apple it any where in our project

11- contructor dependency injection design pattern (data.servise.ts => sharing data)   before angular 15
    - it solve class dependency problem 
        -- when create instance from class in another class inside constracton {let dataService = new DataService}
        -- problem => if service want to a parameter we must send it at all componenets
    - it not use with all class but it use with @Injectable class
    - it inject from class only
    - it solve class dependency problem => when create instance from class in another class

11- function based injection (data.servise.ts => sharing data)   after angular 15
    - by useing inject() function
    - it solve class dependency problem => when create instance from class in another class
    - it solve inheritance at class => we must send property _DataService for super(_DataService)
    - it set initial value in constructor and outside contructor, but not set initial value at any functions=> return Error
    - it inject from class and function

12- Reactive from
    - for complix form with validation
    - scabilaty, reusable, testable
    - we do validation by validetor object
    - new FormGroup({name: new FormControll(this.name,[Validator.required,...]) }) => at componenet.ts
    - [formGroup]="" at form tag=> formControllName="" at input tag => at componenet.html
    
13- template driven form
    - basic form contain one input
    - it depend on two way data binding
        -- name attribute and ngModel and ngSubmit => handle operation at method in componenet.ts


14- global object browser => it is object related browser
    - window, localStorage, location, document
    - we can not use it at Guard and lifeCycle (SSR) => because server not have that global object
    - we can use it in methods
    - solution 1 => check typeof globalObject !== 'undefined'
    - solution 2 => PlatForm Id service => it return id for now PlatForm(browser , server) then we pass id to 'isPlatformBrowser(PlatFormId)' function to ckeck PlatForm browser return true if server return false
    - solution 2 => PlatForm Id service => it return id for now PlatForm(browser , server) then we pass id to 'isPlatformServer(PlatFormId)' function to ckeck PlatForm server return true if server return false
    - solution 3 => use afterRender(()>=>{}), afterNextRender(()=>{}) in constructor or global class (non recommended)

15- promise vs Observable
    - promise => we can not remove it from memory RAM
    - Observable => we can remove it from memory RAM by unsubscribe()

16- pipe (|) => it use for modify on string

17- signal => it use to rerender only part (property) that done action without rerender all componenet
    - comput() => 
        - it must call it at html to rerender , it used make property signal depend on some of property signal computed(()=> this.price() * this.quantity())
    - effect() 
        - it must not call it at html to rerender, use it at contructor, it used to do logic whe occur change at signal , we use it at constructor
        - do logic depend on signal
    - to deal with methods
        1- nameProperty.set(valu) => to reassign for new value
        1- nameProperty.update((valu)=vale+1) => to update for new value
        1- nameProperty() => to get date

18- snapshot VS subscribe at ActivatedRouter
    - snapshot => we do change at url (product id) at the same page => product Id not Change
    - subscribe => we do change at url (product id) at the same page => product Id will be Change (live) it best

19- pipes => it is chennal to transform data
    - purePipe VS imPurePipe
    - we do import for pipe at file.ts

20- interCeptors => it is getway(بوابه) between client and server to deel with requests and responses
    - we can use it ot handle headers of requests, Errors and loading
    - we must talk copy from req (req=req.clone()) until occur orror

21- we use Render2 service for deel with html element
    - but will appeare error becauase it not work at files services => we should use "RendererFactory2"
    - we use it to improve from scuirty

22- lazyloading for parts => effect at SSR (bad)
23- lazyloading for commponent => not effect at SSR

24- input signal
    - namedvarible:InputSignal<string>=input() || input.required()
    - when deal with it => .set, .update(), ()

25- guards => 
  - return boolean value
  - go to app.route.ts to apply routeing for all router by [CanActivate, CanActivateChild, Candeactivate, CanMatch]
  - CanActivate
    -- this normal for router
  - CanActivateChild
    -- can active for child for router
    -- depend on CanActivate
  - Candeactivate
    -- can leave from router or not
  - CanMatch
   -- related loazy loading
