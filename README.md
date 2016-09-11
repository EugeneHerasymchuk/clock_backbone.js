# clock_backbone.js
A simple clock on your web-page, using backbone.js library.
```javascript
var RefreshView = Backbone.View.extend({
    initialize: function () {
        this.model.on('change', function () {
            this.render();
        }, this); // add this to set context, when  event handler function is called
    },
    render: function () {
        this.$el.html(this.model.get('text'));
    }
});

var modelClock = new Backbone.Model({text: new Date().toString()});
var viewClock = new RefreshView({model: modelClock, el: 'body'});
viewClock.render();

setInterval(function () {
    modelClock.set({text: new Date().toString()});
}, 1000);
```
