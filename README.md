LazyStorage is an abstraction layer for indexeddb and webdb
```javascript
var lz = new LazyStorage('Spreeuw',1,{
        {
            'Waarnemingen' : {
                'name': 'Waarnemingen'
            }
        }
    }
);

//save record
$("#obsform").on("submit",function(e) {
    e.preventDefault();
    var data = $(this).serializeObject();
    lz.save("Waarnemingen",data)
});
//delete record
lz.delete("Waarnemingen",{'guid':$("#record_options").data("guid")},function(e) {
    $( "#record_options" ).popup( "close" );
    $( "body" ).pagecontainer("change",$("#waarnemingen"),{'allowSamePageTransition': true });
});
//get all
lz.getAll("Waarnemingen",function(records) {
});
//update
lz.update("Waarnemingen",record,function(record) {

});
