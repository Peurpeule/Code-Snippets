// Scroll top mobile
    $(document).ready(function() {
        function scroll_to_top(div) {
            $(div).click(function() {
                $('html,body').animate({scrollTop: 0}, 'slow');
            });
            $(window).scroll(function(){
                if($(window).scrollTop() > 800){
                    $(div).addClass('active');
                } else{
                    $(div).removeClass('active');
                }
            });
        }
        scroll_to_top(".mobile-page-top");
    });
