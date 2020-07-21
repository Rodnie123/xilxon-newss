$( document ).ready(function() {
    var wave = $('#wave');
    var h = $(document).height();
    var w = $(document).width();

    wave.css('width', w);
    wave.css('height', h);

    wave.delay(500).animate({left: w+300+'px'}, 'slow', function() {
        wave.hide();
    });

    $(".account-btn-1").hover(function(){
        $(".account-btn-1").not(this).each(function(){
            $(this).addClass('gray');
        });
    }, function(){
        $(".account-btn-1").each(function(){
            $(this).removeClass('gray');
        });
    });

    $('form').submit(function() {
        $(this).find(".single-click").attr("disabled", true);
    });

    menu_scroll();
    access_scroll();

    $(window).scroll(function() {
        menu_scroll();
        access_scroll();
    });

    function access_scroll() {
        var scroll = $(window).scrollTop();
        var offset = 410;
        if(scroll > offset && !$('#side-access').is(':animated')){
            $('#side-access').stop().slideDown();
        }
        if(scroll < offset && !$('#side-access').is(':animated')){
            $('#side-access').stop().slideUp();
        }
    }

    function menu_scroll() {
        var scroll = $(window).scrollTop();
        var offset = -25;
        var limit = $('.container').height() - 500;
        if(scroll > offset && scroll < limit) $('#main-menu').css('top', scroll-offset+'px');
        if(scroll < offset) $('#main-menu').css('top', '25px');
        if(scroll > limit) $('#main-menu').css('top', limit+'px');
    }

    function limit(element, max) {
        var max_chars = max;
        if(element.value.length > max_chars) {
            element.value = element.value.substr(0, max_chars);
        }
    }

    $(".auth-tabs .tab").click(function(){
        $(".auth-tabs .tab").each(function(){
            $(this).removeClass('active');
        });
        $(this).addClass('active');

        if($(this).data('form') == 'form-1' && $(this).hasClass('active')){
            $("#form-2").animate({"left":'480px'}, { queue: false, duration: 500 });
            $("#form-2").animate({opacity:0}, { queue: false, duration: 500 });
            $("#form-1").animate({"left":'0'}, { queue: false, duration: 500 });
            $("#form-1").animate({opacity:1}, { queue: false, duration: 500 });
            $("#form-2").removeClass('active');
            $("#form-1").addClass('active');

        }else{
            $("#form-1").animate({"left":'-480px'}, { queue: false, duration: 500 });
            $("#form-1").animate({opacity:0}, { queue: false, duration: 500 });
            $("#form-2").animate({"left":'0'}, { queue: false, duration: 500 });
            $("#form-2").animate({opacity:1}, { queue: false, duration: 500 });
            $("#form-1").removeClass('active');
            $("#form-2").addClass('active');

        }

        var divHeight = $('.auth-forms .active').height();
        $('.auth-forms').css({'height' : divHeight});
    });

    $(".panel").click(function(){
        if($(this).hasClass('active')){
            $(this).removeClass('active');
        }else{
            $(".panel").each(function(){
                $(this).removeClass('active');
            });
            $(this).addClass('active');
        }
    });

    if($(".help-block").length){
        $("html, body").scrollTop($(".help-block").parent().offset().top-100);
    }

    $(".open-modal").click(function(){
        var check = false;
        var response = jQuery.parseJSON($.ajax({
            url: '/auth-check',
            async: false
        }).responseText);
        check = response.check;
        if(check){
            $('#mainModal').appendTo("body").modal('show');
            $('#iframe-1').width(0);
            $('#iframe-1').height(0);
            $('#iframe-1').attr('src', '/'+$(this).data('url')).one("load",function(){
                $('#iframe-1').height($('#iframe-1').contents().height());
                $('#iframe-1').width($('#iframe-1').contents().width());
            });
        }else{
            parent.location.reload();
        }
    });

    $(".modal-dialog").click(function(){
        $('#mainModal').modal('hide');
    });

    var msg = $(".msg-container");
    if(msg.length){
        msg.find('.timeout').css('width', '100%');
        setTimeout(
            function()
            {
                msg.slideUp('slow');
            }, 6000);
    }

    $(document).on('input propertychange', '.contacts-text', function () {
        var o = $('.contacts-text');
        o.css('height', '40px');
        o.css('height', o.prop('scrollHeight')+"px");
    });

    var siri = document.getElementById('siri-container');
    if(siri){
        var siriWave = new SiriWave({
            container: siri,
            width: 400,
            height: 50,
            speed: 0.02,
            color: '#032b8d',
            frequency: 6
        });

        siriWave.start();
    }


    var tabID = sessionStorage.tabID && sessionStorage.closedLastTab !== '2' ? sessionStorage.tabID : sessionStorage.tabID = Math.random();
    sessionStorage.closedLastTab = '2';
    Cookies.get("tab") ? '' : Cookies.set("tab", tabID);
    $(window).on('unload beforeunload', function() {
        sessionStorage.closedLastTab = '1';
        Cookies.remove("tab")
    });
    var audio = document.getElementById('audio-track');
    if(audio){
        var time = Cookies.get("music");
        if(time <= 109.3){
            audio.currentTime = time;
        }else{
            audio.currentTime = 0;
        }
        audio.volume = 0.1;

        if(Cookies.get("paused") == "true" || Cookies.get("tab") != tabID){
            audio.pause();
            $('#music-toggle').attr('src', '/img/icon-66.png');
            $('#music-toggle').removeClass('active');
        } else{
            audio.play();
        }

        $(window).on('beforeunload', function(){
            Cookies.set("music", audio.currentTime);
            audio.pause();
        });

        $('#music-toggle').click(function(){

            if (!audio.paused) {
                audio.pause();
                Cookies.set("paused", "true");
                $(this).attr('src', '/img/icon-66.png');
                $(this).removeClass('active');

            } else {
                audio.play();
                Cookies.set("paused", "false");
                $(this).attr('src', '/img/icon-65.png');
                $(this).addClass('active');
            }

        });
    }

    var chrt = $("#chart-1");
    if(chrt.length){
        var ctx = document.getElementById("chart-1").getContext("2d");
        var chartData = $("#chart-1").data('data').split(',');

        var gradient = ctx.createLinearGradient(0, 0, 0, 200);
        gradient.addColorStop(0, 'rgba(186,39,204,0.6)');
        gradient.addColorStop(1, 'rgba(82,205,213,0.6)');

        var myChart = new Chart(ctx, {
            type: 'line',
            data: {
                labels: ['','','','','','','','','','','','','','','','','','','','','','','','','','','','','','','','','','','','','','','',''],
                datasets: [{
                    radius: 0.5,
                    pointBackgroundColor: ['rgba(186, 39, 204 ,0)'],
                    pointHoverBackgroundColor: ['rgba(186, 39, 204 ,0)'],
                    pointBorderColor: 'rgba(186, 39, 204 ,0)',
                    pointHoverBorderColor: 'rgba(186, 39, 204 ,0)',
                    label: '$',
                    data: chartData,
                    backgroundColor: gradient,
                    borderColor: [
                        'rgba(186, 39, 204 ,1)'
                    ],
                    borderWidth: 1,
                    // steppedLine: true
                }]
            },
            options: {
                tooltips: {
                    displayColors: false,
                    enabled: true,
                    mode: 'single',
                    callbacks: {
                        label: function(tooltipItems, data) {
                            return '$'+tooltipItems.yLabel;
                        }
                    }
                },
                legend: {
                    display: false
                },
                scales: {
                    yAxes: [{
                        gridLines: {
                            color: "#f1f1f1"
                        },
                        display: false,
                        ticks: {
                            beginAtZero:false
                        }
                    }],
                    xAxes: [{
                        display: false,

                        gridLines: {
                            color: "#f1f1f1"
                        },
                        ticks: {
                            autoSkip: true
                        }
                    }]
                }
            }
        });
    }

    var Tawk_API=Tawk_API||{}, Tawk_LoadStart=new Date();
    (function(){
        var s1=document.createElement("script"),s0=document.getElementsByTagName("script")[0];
        s1.async=true;
        s1.src='https://embed.tawk.to/5bceb9c6476c2f239ff592e3/default';
        s1.charset='UTF-8';
        s1.setAttribute('crossorigin','*');
        s0.parentNode.insertBefore(s1,s0);
    })();
});

function limit(limitField, limitNum) {
    if (limitField.value.length > limitNum) {
        limitField.value = limitField.value.substring(0, limitNum);
    }
}