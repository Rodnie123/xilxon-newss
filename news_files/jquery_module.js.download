$(document).ready(function(){

    var swiper = new Swiper('.swiper-container', {
        slidesPerView: 2,
        spaceBetween: 30,
        slidesPerGroup: 1,
        loop: true,
        loopFillGroupWithBlank: true,
        pagination: {
            el: '.swiper-pagination',
            clickable: true,
        },
        navigation: {
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev',
        },
        breakpoints: {
            // when window width is <= 320px
            1199: {
                slidesPerView: 1,
                spaceBetween: 10
            }
        }
    });

    var swiper = new Swiper('.swiper-container-2', {
        slidesPerView: 2,
        spaceBetween: 30,
        slidesPerGroup: 1,
        loop: true,
        loopFillGroupWithBlank: true,
        navigation: {
            nextEl: '.swiper-button-next-2',
            prevEl: '.swiper-button-prev-2',
        },
        breakpoints: {
            // when window width is <= 320px
            1199: {
                slidesPerView: 1,
                spaceBetween: 10
            }
        }
    });

    var swiper = new Swiper('.swiper-container-3', {
        slidesPerView: 3,
        spaceBetween: 30,
        slidesPerGroup: 1,
        loop: true,
        loopFillGroupWithBlank: true,
        navigation: {
            nextEl: '.swiper-button-next-2',
            prevEl: '.swiper-button-prev-2',
        },
    });


    $( ".h-section-three .change-val .button-change-val" ).on("click", function () {

        $(".h-section-three .change-val .button-change-val").removeClass("active");
        value = $(this) .data('value');
        $(".h-section-three .change-val .button-change-val[data-value="+value+"]").addClass("active");

    });

    $("a[href^='#']").click(function(e) {
        e.preventDefault();

        var position = $($(this).attr("href")).offset().top;

        $("body, html").animate({
            scrollTop: position
        }, 1000 );

    });





});