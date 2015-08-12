LazyStorage
===========================

LazyStorage is an abstraction layer for indexeddb and webdb.


## Usage
```javascript
var lz = new LazyStorage('Spreeuw',1,{
        {
            'Waarnemingen' : {
                'name': 'Waarnemingen'
            }
        }
    }
);
```
The constructor takes database name, version and a schema object as arguments. The schema object can be
an array of table descriptions. Each description is an object with at least the property name
```javascript
[
  {
    'name' : 'Tiles'
  }
]
```

Operations
```javascript
//save record
$("#obsform").on("submit",function(e) {
    e.preventDefault();
    var data = $(this).serializeObject();
    lz.save("Waarnemingen",data,function(record) { })
});
//delete record
lz.rm("Waarnemingen",{'guid':$("#record_options").data("guid")},function(e) {
    $( "#record_options" ).popup( "close" );
    $( "body" ).pagecontainer("change",$("#waarnemingen"),{'allowSamePageTransition': true });
});
//get all
lz.getAll("Waarnemingen",function(records) {
});
//update
lz.update("Waarnemingen",record,function(record) {

});
