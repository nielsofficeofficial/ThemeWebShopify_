# Theme Website Development Shopify
References Shopify Development 

<a href="https://github.com/nielsofficeofficial/shopify-sections"> Section References </a> <br />
<a href="https://github.com/nielsofficeofficial/shopify-tutorial"> Tutorial References </a> <br />
<a href="https://github.com/nielsofficeofficial/Celeste"> Liquid References </a> <br />

<h4> Reference Development </h4>
<a href="https://shopify.github.io/liquid/"> Liquid References Dev </a> <br />
<a href="https://www.shopify.com/partners/shopify-cheat-sheet/"> Partners Cheat Sheet Dev </a> <br />
<a href="https://shopify.dev/api/liquid"> Liquid API Dev </a> <br />
<a href="https://shopify.dev/api/liquid/basics"> Liquid API Basic Dev </a> <br />
<a href="https://shopify.dev/api/liquid/tags"> Liquid API Tags Dev </a> <br />
<a href="https://shopify.dev/api/liquid/filters"> Liquid API FIlters Dev </a> <br />
<a href="https://shopify.dev/api/liquid/objects"> Liquid API Objects Dev </a> <br />

<h4> Theme Development </h4>

```Liquid

> Sections [ folder ]
// create a custom section
// Section:  Display Page name
// Ypu can work with Object|Tags|filter 

<h1> {{ page.title }} </h1>

{% schema %}
 {
   "name" :  "Custom Section Display Page Name",
   "settings" : [{
      
       "id" : "Custom-Section-Page-Name",
       "Type" : "Text",
       "Label": "Display Page title through this custom section"      
 
   }],
  "templates" : ["index", "page","pageName"] // use this line of you want this avaialble only on that particular pages
  "presets" : [{
       "name" : "Custom Section Display Page Name",
       "Category" : "Reference"
   }]
 }
{% endschema %}

// Redndering the text Type get by ID from settings : 
 <h1> {{ section.settings.Custom-Section-Page-Name }} </h1>

```

```Liquid

// Multiple field
// https://shopify.dev/themes/architecture/settings/input-settings
// https://youtu.be/ejXm7CMGH6Y?t=6626

{% schema %}
 {
   "name" :  "Custom Section Display Page Name",
   "settings" : [{
      
       "id" : "Custom-Section-Page-Name",
       "Type" : "Text",
       "Label": "Display Page title through this custom section"      
 
   },
   {
      
       "id" : "Custom-Section-Page-Name-box",
       "Type" : "checkbox",
       "Label": "Display Page title through this custom section"      
 
   }
  ],
  "templates" : ["index", "page","pageName"] // use this line of you want this avaialble only on that particular pages
  "presets" : [{
       "name" : "Custom Section Display Page Name",
       "Category" : "Reference"
   }]
 }
{% endschema %}

 // Redndering the text Type get by ID from settings : 
 <h1> {{ section.settings.Custom-Section-Page-Name }} </h1>

```

```Liquid

// Repeater or block

{% schema %}
 {
   "name" :  "Custom Section Display Page Name",
   "settings" : [{
      
       "id" : "Custom-Section-Page-Name",
       "Type" : "Text",
       "Label": "Display Page title through this custom section"      
 
   },
   
  ],
  "presets" : [{
       "name" : "Custom Section Display Page Name",
       "Category" : "Social"
   }],
   "blocks": [
     {
       "name": "SocialMedia",
       "Type": "social-netkwork",
       "settings" : [
	   
         {           
           "id": "id-name",
           "type": "text",
           "label": "Social Media Name"	
         }	
            
       ]
     }
   ]
  }

{% endschema %}

 // rendering block | repeater

 {% for block in section.blocks %}

  {{ block.settings.id-name}}
  
 {% endfor %}

```
