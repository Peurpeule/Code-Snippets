
```javascript
/* SMOOTH SCROLL TO ANCHOR */
$('.anchor').on('click', function() {
    let page = $(this).attr('href');
    $('html, body').animate( { scrollTop: $(page).offset().top }, 750 );
    return false;
});
```
