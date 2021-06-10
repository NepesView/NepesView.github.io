// 부스 로그인 
var lay_Booth_Open = function (_menu) {
    // _menu(1) : /booth/booth_gib_read.asp, _menu(2) : /booth/booth_gi_info_read.asp, menu(3) : /Text_User/Resume/Resume_Step1.asp

    var menugbn = _menu;

    var _data = {
        GI_No: gino,
        C_ID: cid,
        PageGbn: pagegbn,
        MenuGbn: menugbn,
        Oem_Code : Site_Oem_Code
    }

    jQuery.ajax({
        type: "post",
        url: "/Booth/Booth_Login.asp",
        data: _data,
        success: function (data) {
            lay_Booth_Cls();

            // 레이어 위치 조절 전 hide 대신 좌측으로 넘겼다가 가져옴.
            // hide 실행시 해당 div의 height 조절 못함

            jQuery("body").append(data).find("div.layerBooth").css("left", "-9999px");

            lay_Booth_Frm_Size();
        },
        error: function (xhr) {
            //				alert(xhr.message);
        }
    });

    return false;
}

// 부스 로그인_HR
var lay_Booth_HR_Open = function (_menu) {
    // _menu(1) : /booth/booth_gib_read.asp, _menu(2) : /booth/booth_gi_info_read.asp, menu(3) : /Text_User/Resume/Resume_Step1.asp

    var menugbn = _menu;

    var _data = {
        GI_No: gino,
        C_ID: cid,
        PageGbn: pagegbn,
        MenuGbn: menugbn,
        Oem_Code : Site_Oem_Code
    }

    jQuery.ajax({
        type: "post",
        url: "/Booth/Booth_Login.asp",
        data: _data,
        success: function (data) {
            lay_Booth_Cls();

            // 레이어 위치 조절 전 hide 대신 좌측으로 넘겼다가 가져옴.
            // hide 실행시 해당 div의 height 조절 못함

            jQuery("body").append(data).find("div.layerBooth").css("left", "-9999px");

            lay_Booth_HR_Frm_Size();
        },
        error: function (xhr) {
            //				alert(xhr.message);
        }
    });

    return false;
}

// 레이어 닫기
var lay_Booth_Cls = function () {
    jQuery("div.layerBooth").remove();
}

// 레이어 닫기 유형 2(alert)
var lay_Booth_Cls2 = function (_str) {
    alert(_str);
    jQuery("div.layerBooth", parent).remove();
}

// 레이어 로그인 IP 보안
var lay_Booth_Ip_Chk_Set = function () {
    var jQueryobj = jQuery("button.btnSecurity");

    var today = new Date();
    var expire = new Date(today.getTime() + 60 * 60 * 24 * 30 * 1000);

    var IPSecCookie = "Secure_IPonOFF="

    if (jQueryobj.hasClass("setOn")) {
        jQueryobj.toggleClass("setOn setOff").text("OFF");
        jQueryobj.next().removeClass("devHide");
        IPSecCookie += escape("N");
    } else {
        jQueryobj.toggleClass("setOff setOn").text("ON");
        jQueryobj.next().addClass("devHide");
        IPSecCookie += escape("Y");
    }

    IPSecCookie += "; expires=" + expire.toGMTString() + "; path=/; domain=jobkorea.co.kr;";
    document.cookie = IPSecCookie;
}

// 프레임 사이즈 - Ajax 호출시
var lay_Booth_Frm_Size = function () {
    var jQueryheight = 0;
    var jQueryobj = jQuery("#Booth_Login");

    if (jQueryobj.attr("src").toLowerCase().indexOf("booth_frame_login.asp") > -1 || jQueryobj.attr("src").toLowerCase().indexOf("m_login_layer") > -1) {
        jQueryheight = jQueryobj.height();
        lay_Booth_Size_Chg(jQueryheight);
    }
}

// 프레임 사이즈 - Ajax 호출시
var lay_Booth_HR_Frm_Size = function () {
    var jQueryheight = 0;
    var jQueryobj = jQuery("#Booth_Login");

    if (jQueryobj.attr("src").toLowerCase().indexOf("booth_frame_login.asp") > -1 || jQueryobj.attr("src").toLowerCase().indexOf("m_login_layer") > -1) {
        jQueryheight = jQueryobj.height();
        lay_Booth_HR_Size_Chg(jQueryheight);
    }
}

//	프레임 리사이즈
var lay_Booth_Size_Chg = function (_height) {
    var jQuerydiv = jQuery("body").find("div.layerBooth");
    var jQueryobj = jQuery("#Booth_Login");

    jQueryobj.css("height", _height);

    // IE 구버전 처리
    var isIE = navigator.userAgent.toLowerCase().indexOf("msie") !== -1;

    if (isIE) {
        var $width = window.innerWidth ? window.innerWidth : $(window).width();
        var $height = window.innerHeight ? window.innerHeight : $(window).height();

        var jQueryleft = jQuery(window).scrollLeft() + ($width - jQuerydiv.width()) / 2;
        var jQuerytop = jQuery(window).scrollTop() + ($height - jQuerydiv.height()) / 2;
    } else { // 모바일 사파리에서 window 사이즈 틀리게 나와서 window.top으로 수정
        var topWindow = window.top;
        var $width = topWindow.innerWidth ? topWindow.innerWidth : jQuery(topWindow).width();
        var $height = topWindow.innerHeight ? topWindow.innerHeight : jQuery(topWindow).height();

        var scrollTop = jQuery(window).scrollTop();
        var scrollLeft = jQuery(window).scrollLeft();

        if (scrollTop === 0) {
            scrollTop = jQuery(topWindow).scrollTop();
        }
        if (scrollLeft === 0) {
            scrollLeft = jQuery(topWindow).scrollLeft();
        }

        var jQueryleft = scrollLeft + ($width - jQuerydiv.width()) / 2;
        var jQuerytop = scrollTop + ($height - jQuerydiv.height()) / 2;
    }

    jQuerydiv.css({
        "position": "absolute",
        "z-index": "999999",
        "left": jQueryleft,
        "top": jQuerytop
    });
}

//	프레임 리사이즈
var lay_Booth_HR_Size_Chg = function (_height) {
    var jQuerydiv = jQuery("body").find("div.layerBooth");
    var jQueryobj = jQuery("#Booth_Login");

    jQueryobj.css("height", _height);

    var $width = window.innerWidth || document.documentElement.clientWidth || document.body.clientWidth;
    var $height = window.innerHeight || document.documentElement.clientHeight || document.body.clientHeight;

    var jQueryleft = jQuery(window).scrollLeft() + ($width - jQuerydiv.width()) / 2;
    var jQuerytop = jQuery(window).scrollTop() + ($height - jQuerydiv.height()) / 2;

    jQuerydiv.css({
        "position": "absolute",
        "z-index": "999999",
        "left": jQueryleft,
        "top": jQuerytop
    });
}

// 로그인 레이어 focus 이벤트
var lay_Booth_Login_Fcs = function (_this) {
    var jQueryobj = jQuery("p.loginInput").find("input.inpTxt");
    var jQuerythis = jQuery(_this);

    jQuerythis.addClass("on");

    if (jQuerythis.hasClass("inpTxt inpID")) {
        jQueryobj.eq(1).removeClass("on").addClass("off");
    } else {
        jQueryobj.eq(0).removeClass("on").addClass("off");
    }

    jQuerythis.one("blur", function () {
        if (jQuery.trim(jQuerythis.val()) != "") {
            jQuerythis.removeClass("off").addClass("end");
        } else {
            jQuerythis.val("");
            jQuerythis.removeClass("end").addClass("off");
        }
    });
}

// 로그인 처리
var login_Send = function () {

    if (jQuery.trim(jQuery("#M_ID").val()) == "") {
        alert("아이디를 입력하세요.");
        jQuery("#M_ID").val("").focus();
        return false;
    }

    if (jQuery.trim(jQuery("#M_PWD").val()) == "") {
        alert("비밀번호를 입력하세요.");
        jQuery("#M_PWD").val("").focus();
        return false;
    }

    if (document.form_login.DB_Name.value == "GI") {
        document.form_login.LoginPage.value = window.jkDomain + "/Login/Login_GI.asp";
    }
    else {
        document.form_login.LoginPage.value = window.jkDomain + "/Login/Login_GG.asp";
    }
}