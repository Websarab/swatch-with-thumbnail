# swatch-with-thumbnail

 //custom feature product
$('input.custom_color_swatch').click(function(){
var color_val_get = $(this).val().toLowerCase();
$('.product_image_sidebar_items').each(function(){
var product_image_alt = $(this).find('.product_image_sidebars').attr('alt').toLowerCase();
var match_variants_content = product_image_alt.includes(color_val_get);
if(match_variants_content == true){
 
 $(this).trigger("click" );
$(this).addClass('testcode');
}else{
console.log('no');
}

});

})

 <div class="main">
     <div class="slider slider-nav product_image_sidebar">
     {% for image in product.images %}
           {% for variant in image.variants %}
             <div class="item product_image_sidebar_items">
             <img class="test1 product_image_sidebars" src="{{variant.image.src | img_url: '100x100'}}"
                        alt="{{variant.title}}"/>
                 </div>
           {% endfor %}
       {% endfor %}
    </div>
  
     <div class="slider slider-for single_product_images_main">
         {% for image in product.images %}
                   
                       <img class="test single_product_image" src="{{image | img_url: '800x800'}}"
                        alt="{{image.alt}}"/>
           {% for variant in image.variants %}
             <div class="item single_product_images">
             <img class="test single_product_image" src="{{variant.image.src | img_url: '800x800'}}"
                        alt="{{variant.title}}"/>
                 </div>
           {% endfor %}
       {% endfor %}
     </div>
   
  </div>
  
  
   $('.slider-for').slick({
   slidesToShow: 1,
   slidesToScroll: 1,
   arrows: false,
  dots: true,
   fade: true,
   asNavFor: '.slider-nav'
 });
 $('.slider-nav').slick({
   slidesToShow: 4,
   slidesToScroll: 1,
   asNavFor: '.slider-for',
   dots: false,
   vertical: true,
   focusOnSelect: true
 });
