A simple filter functionallity created with Vanilla JavaScript, HTML and CSS. 

A few notes: 
1. The project is not responsive
2. JavaScript code is inside index.html since the project is small.

How does it work?

We have two parts:
1. Adding all products
2. Filter the products

*First part - adding the products to the page:*

We create an array.

All products are stored inside the array as objects

let products = [
      {
        image: "./images/breakfast/proteinPancakes.jpg",
        title: "Протеинови Палачинки с плодове и кленов сироп",
        price: "9.90",
        description: "Палачинки с високо съдържание на протеин за спортисти и хора целящи влизането в по-добра форма.",
        category: "breakfast"
      },

]

Every product has a category!!!

We use a for loop that loops though all products using: products.length 
and add all products to the page with property priceTag.insertAdjacentHTML('beforeend', *here you add your html code*);

for (let i = 0; i < products.length; i++) {

      priceTag.insertAdjacentHTML('beforeend', `
        <div class="products">

        <img class="prodImages" src="${products[i].image}">
        <h3 class='headers'>${products[i].title}</h3>
        <p class="price">${products[i].price}</p>
        <p class="info">${products[i].description}</p>

      </div>`);


    }

  In that way all products are dynamically generated.

*Second part - filtering the products:*

We take all the filter buttons and store them in a variable:

    let all = document.querySelector('.All');
    let breakfast = document.querySelector('.Breakfast');
    let lunch = document.querySelector('.Lunch');
    let dinner = document.querySelector('.Dinner');
    let deserts = document.querySelector('.Deserts');

At this point we need to create the functionality with the filter: 

      let selectedData = products.filter(value => {
        return value.category === "breakfast";
      });

      
This piece of code returns only the objects where the category is equal to "breakfast". 
.filter() is a built in function in JavaScript (Google it if you need more info about the syntax)
We do the same for the rest of the products where the categories are different. (check the code).

Now we add the click event with addEvenetListener('click') when we click button "Breakfast" for example.

breakfast.addEventListener('click', function () {

      let selectedData = products.filter(value => {
        return value.category === "breakfast";
      });

      priceTag.innerHTML = '';

      selectedData.forEach(element => {

        priceTag.insertAdjacentHTML('beforeend', `
        <div class="products">
        <img class="prodImages" src="${element.image}">
        <h3 class='headers'>${element.title}</h3>
        <p class="price">${element.price}</p>
        <p class="info">${element.description}</p>
      </div>`);

      });

    })

  This piece of code is basically doing the following: 
  1. Retruns all objects where the category is "breakfast"
  2. priceTag.innerHTML = ''; this code removes all products from the screen.
  3. priceTag.insertAdjacentHTML() adds the products to the screen only where the category is breakfast.

And thats how the filter is done. 

We always remove all products from the screen before adding the filtered ones. 




