#### Routes
**/department/:id/:groceryId** ensureLoggedIn('/auth/account'), departmentController.getDepartment);

**/departments/show/:groceryId** 		ensureLoggedIn('/auth/account'),	 departmentController.departmentsList);

// :todo make it work 
**/hide/department/:id/:groceryId**

**/show/department/:id/:groceryId**

**/show/all/:groceryId** 

**/visibility/department/:id/:groceryId** 

**/remove/department/:id/:groceryId** departmentController.deleteDepartment);

----

router.get('**/favorites**', ensureLoggedIn('/auth/account')


  router.post('**/delete/favorites/**', ensureLoggedIn('/auth/account')



  router.get('**/add/fav2/:ingredientId**', ensureLoggedIn('/auth/account')

    

  router.get('**/add/fav2/clear**',  ensureLoggedIn('/auth/account')

---

  **/view/grocery/:groceryId**     
    ensureLoggedIn('/auth/account'),
    groceryController.viewGrocery);


  // :todo Handle this later. just want to fix issue fast.
  // This is a clone of /view/grocery functionality for reviewing
  // as not logged in user a data from ultimate grocery list
  // for simplifying things i'll just duplicate a lot stuff
  // and make it work as quicker as i can
  router.get('**/view/ultimategrocery/**',
    groceryController.viewUltimateGrocery);

 router.get('**/view/grocery/hidden/:groceryId**',
  ensureLoggedIn('/auth/account'),
  function(req, res, next){
    var Grocery   = app.models.Grocery;
    var groceryId = req.params.groceryId;

    // only hidden departments will be diplsayed
    Grocery.fetchById2(groceryId, function(err, response){

      // console.log(response);

      // :todo make all data came from method
      res.render('pages/grocery', {
          name: 'Hidden departments of ' + response.name,
          departments: response.data, // [data>> department >> ingredient]
          groceryId: groceryId,
          messages: {},

      });

    });

  });



  router.get('**/auth/attach-grocery-to-user/:groceryId**',
    ensureLoggedIn('/auth/account'),
    function(req, res, next) {
    var groceryId = req.params.groceryId;
    var userId    = req.user.id;
    var User      = app.models.user;
    var Grocery   = app.models.Grocery;

    // this is a duplicated function from Grocery :todo think about it, real talk
    var options = {
      userId: userId,
      secondArray: [ groceryId ]
    };
    User.addGrocery(options);
    // User.proceed(options);

    res.redirect('/auth/account');
  });



 router.get('**/remove/grocery/:groceryId**',
  ensureLoggedIn('/auth/account'),
  groceryController.removeGrocery);




  router.get('**/clone/:groceryId**', groceryController.cloneGrocery);

  router.post('**/cloneform**', groceryController.postCloneForm);

  router.get('**/afterclone**', groceryController.justRedirect);

  router.get('**/clone-grocery/:groceryId**', groceryController.getCloneForm);



// :todo finish
 router.get('**create-new-grocery**',
  ensureLoggedIn('/auth/account'),
  groceryController.createNewGrocery);

// :todo finish Not used functionality right now
 router.get('**/view/groceries**',
  ensureLoggedIn('/auth/account'),

 // Change Grocery Name functionality

 router.get('**/change/grocery/name/:groceryId**',
  ensureLoggedIn('/auth/account'),
  groceryController.changeName);

  // Update grocery list name
  router.post('**/update/name**',
    groceryController.postUpdateName);


  // Shopping part, i.e. TODO list
  router.get('**/shopping/:groceryId/:departmentId**',
    groceryController.shopping);



// :todo this must be a remote method
  // Ing create. Not working with not advanced forms
  router.post('**/create/ing/**', 



  // Ing change name
  router.post('**/changename/**', 



    router.get('/add/ing/:id/:groceryId', 


  // Ing change Department ID
  router.get('**/changedepartmentid/:id/:departmentId**', 


    ----


router.post('**/togglepurchased**', 


  router.post('**/clearpurchased**', 


  // used for ajax call from todo list
  // :todo maybe move to shopping controller, for easy keeping all things in one place?
  router.post('**/unattach**'


#### Release 1 pages, layouts, etc. hope names makes it more clear
```Views
  forms
     clear-purchased
     clone-grocery
     grocery
     purchased
     unpurchased
     update-name

  layouts
    dashboard
    grocery
    homepage
    jquery
    landos
    layout - main
    material-layout
    selectable

  pages
    --departments
    --grocery
      --clone-form-page
      --view-grocery-new
      --view-grocery
      --view-ultimate-List
    --shopping
    --static
      --credits
      --Landing
      --privacy
      --terms

    account
    change-grocery-list-name
    clear-page
    dashboard
    department
    favorites
    grocerylist
    homepage
    index
    ingredient
    lastgrocery
    login
    manage-grocerylist
    printgrocery
    purchased
    signup
```




![XXX](https://github.com/GroceriStar/creative/blob/master/prev.%20design.screens/Shopping%20List%20%2059f1695cd534650012ae0ee7%20(1).png)


![XXX](https://github.com/GroceriStar/creative/blob/master/prev.%20design.screens/Shopping%20List%20%2059f1695cd534650012ae0ee7.png)



![XXX](https://github.com/GroceriStar/creative/blob/master/prev.%20design.screens/groceristar%20herokuapp%20com%20auth%20account%20_%20_%20(1).png)


![XXX](https://github.com/GroceriStar/creative/blob/master/prev.%20design.screens/groceristar%20herokuapp%20com%20auth%20account%20_%20_%20(2).png)

![XXX](https://github.com/GroceriStar/creative/blob/master/prev.%20design.screens/groceristar%20herokuapp%20com%20departments%20show%205a6fb00ef3909e0012274dab%20(1).png)

![XXX](https://github.com/GroceriStar/creative/blob/master/prev.%20design.screens/groceristar%20herokuapp%20com%20departments%20show%205a6fb00ef3909e0012274dab.png)


![XXX](https://github.com/GroceriStar/creative/blob/master/prev.%20design.screens/groceristar%20herokuapp%20com%20view%20grocery%205a6fb00ef3909e0012274dab.png)


![XXX](https://github.com/GroceriStar/creative/blob/master/prev.%20design.screens/groceristar%20herokuapp%20com%20view%20ultimategrocery%20%20(1).png)


![XXX](https://github.com/GroceriStar/creative/blob/master/prev.%20design.screens/groceristar%20herokuapp%20com%20view%20ultimategrocery%20.png)


![XXX](https://github.com/GroceriStar/creative/blob/master/prev.%20design.screens/groceristar%20herokuapp%20com%20auth%20account%20_%20_.png)


![XXX](https://github.com/GroceriStar/creative/blob/master/prev.%20design.screens/Shopping%20List%20%205a6fb00ef3909e0012274dab.png)
