# Ukay (Buyer App - Front End Documentation)


## Home Page

This is the main inspiration of the home page that we will build for our product.

***Notes***

 - [ ] Almost retain all the UI elements just change the icon to our brand logo.
 - [ ]  *`Designers`* label will be changed to *`Brands`*, and that component shall be a dropdown that contains trending brands.
 - [ ]  There shall be an advertisement banner component sa place ng *Aarong Farniture Set* na nag-iislide like every 10 seconds automatically.
 - [ ]  As is yung *`trending products`*,  `latest additions`, tapos dagdagan na rin ng *`trending categories`*
 - [ ]  If may *`sale or percent off`* sa price display nalang beside sa original price yung *`net price`* ( naka emphasize ) and then percent off.
 - [ ]  Display na rin yung brand and then yung seller or shop name.
 - [ ]  For the footer part, basis yung photo number two. Just include yung `work hours`, and then `join us in social networks`. Tapos katulad doon sa photo number one na social icons ganoon ang ilagay.
 - [ ]  *When clicked yung search icon*, dapat mag display ng search box sa taas ng advertisement banners.
 - [ ]  When sign in is clicked go to Sign Up component, cart icon button clicked go to Cart Component.
 - [ ]  Remove the wishlist icon or the heart icon.


![enter image description here](https://cdn.dribbble.com/users/641906/screenshots/6279620/preview2.png)

![enter image description here](https://cdn.dribbble.com/users/2446071/screenshots/13893056/media/6c4483b6765ba17203cefd3d433c35d3.png)


## Products Page

***Notes***
 - [ ] Retain *`Shopping Category`*, *`Brands`*
 - [ ] Include *`Colors`* sa sidebar yung parang sa photo number two.
 - [ ] Include *`Body Type`* sa sidebar.
 - [ ] Sort *`Price: Low to High`* and *`Price: High to Low`*
 - [ ] Include *`Size`* sa sidebar, pero yung mga values neto nakadepend sa *`Shopping Category`*
 - [ ] Yung Product component dapat same lang din sa Home Page.		
![enter image description here](https://cdn.dribbble.com/users/2446071/screenshots/13893056/media/0f58dd2614435fcba84025fc37193018.png)

![enter image description here](https://cdn.dribbble.com/users/195104/screenshots/11323964/media/42d68c0c23230d0d34e2c45224f6e1cf.png)

---

## Product Details

 - [ ] After nung price sa baba include mo yung `Variants` nung product.
 - [ ] Retain mo yung `Select Size` na part pero include mo yung stocks every size. ***Tapos dynamic pala yan dapat kung ano lang yung sizes na available dapat ayun lang yung enabled.***
 - [ ] ***Dagdag na rin yung color*** pagka expand nung `Product Details.`
 - [ ] Retain yung image gallery ng products sa kaliwa.
 - [ ] `Other Products by` section dagdag natin after nung photo number, ***kung saan madi-display yung ibang items ng seller nung item.***
 - [ ] Sa future dagdag din natin after nung Other products section magkaroon tayo ng `Recommended products section`.
 - [ ] Sa future dagdag din yung social media share ng product.

![enter image description here](https://cdn.dribbble.com/users/618212/screenshots/14176331/media/9b8b4bae8db0f1a90234dbd08e3d7675.png)

![enter image description here](https://cdn.dribbble.com/users/618212/screenshots/14176331/media/d8cb443fea17a34f27c1c2a87d1509b5.png)

## Cart

 - [ ] Retain yung same idea na every item naka group by store para mas madali makita nung user.
 - [ ] Remove na yung seller checkout, sidebar sa left side.
 - [ ] Promo codes wala muna.
 - [ ] Yung item number palitan ng sku.
 - [ ] Quantity pwede mag add or minus, pero naka debounce yan kasi magre-request yan sa server para validation narin kung may ganoon na quantity pa ba.
 - [ ] Every change sa quantity dapat nag rere-calculate yung shipping fee.
 - [ ] Pagka checkout rekta na sa 3rd party payment gateway.
 - [ ] Every item clickable para mapunta sa Product Detail page.
 - [ ] Same sa item shop tapos dagdagan narin ng shop image or logo.
 - [ ] Retain yung checkbox.
 - [ ] Yung 3 dots actions yan pero isang action muna which is delete item from cart.
 - [ ] Shipping address section lagay narin dito from photo number 2.
 - [ ] Sa future checkout muna yung button pero in the future parang magiging dropdown na yan kasi magkakaroon tayo ng other gateways.

![enter image description here](https://cdn.dribbble.com/users/576948/screenshots/10721832/media/578b6fc1126adad3458f14b6b0262eed.png)

![enter image description here](https://cdn.dribbble.com/users/576948/screenshots/10730228/media/49d56402faf38e1ca28aea289484a4d2.png)

## User Profile Page

 - [ ] Dagdagan ng `middle name` input field.
 - [ ] My orders na tab, parang nasa gif. Write a Review magiging `Write a Feedback`. Tapos bawat feedback ay per item dapat.
 - [ ] Buy again delete.
 - [ ] Cancel order pwede lang lumitaw kapag `Order placed` palang ang status.
 - [ ] Write a Feedback lilitaw lang kaapg yung status ay `delivered` na.
 - [ ] Bawat items naka group yung order by shop.
 - [ ] Sa baba ng list ng items yung delivery address at contact number.
 - [ ] Sa settings. On / off slider lang ng Two Factor Authentication.

![enter image description here](https://imgur.com/ZbJmoQY.png)

![enter image description here](https://imgur.com/bId1rHB.gif)
