//트위터 연동
var goTwitter = function (TwitterTitle, ShotURL) {
    try {
        //Shorten URL 포스팅수 누적
        goPosting(1);
        //트위터로 전송
        var title = TwitterTitle;
        var ShotURL = ShotURL;
        var LinkPage = "http://twitter.com/intent/tweet?text=" + encodeURIComponent(title);
        var ua = navigator.userAgent.toLowerCase();

        if (ua.indexOf("ipad") != -1) {
            location.href = LinkPage;
        } else {
            window.open(LinkPage, '', '');
        }
    }
    catch (e) {
        alert(e.message);
    }
}

//페이스북 연동
var goFacebook = function (ShotURL) {
    try {
        //Shorten URL 포스팅수 누적
        goPosting(2);
        //페이스북으로 전송
        var ShotURL = ShotURL;
        var LinkPage = "http://www.facebook.com/sharer.php?u=" + encodeURIComponent(ShotURL);
        var ua = navigator.userAgent.toLowerCase();

        if (ua.indexOf("ipad") != -1) {
            location.href = LinkPage;
        } else {
            window.open(LinkPage, 'facebookShare', 'width=740px,height=400px');
        }
    }
    catch (e) {
        //alert(e.message);
    }
}

//미투데이 연동
var goMe2Day = function (C_Name, GI_Subject, Me2DayTitle) {
    try {
        //Shorten URL 포스팅수 누적
        goPosting(3);
        //미투데이로 전송
        var Msg = C_Name + "-" + "\"" + GI_Subject + "\":" + Me2DayTitle;
        var ShotURL = ShotURL;
        var Tag = "채용, 취업, 모임, 일자리";
        var LinkPage = "http://me2day.net/posts/new?new_post[body]=" + encodeURIComponent(Msg) + "&new_post[tags]=" + encodeURIComponent(Tag);
        var ua = navigator.userAgent.toLowerCase();

        if (ua.indexOf("ipad") != -1) {
            location.href = LinkPage;
        } else {
            window.open(LinkPage, '', '');
        }
    }
    catch (e) {
        //alert(e.message);
    }
}

//씨로그 연동
var goCLog = function (Url) {
    try {
        //Shorten URL 포스팅수 누적
        goPosting(4);
        //씨로그로 전송
        var LinkPage = "http://csp.cyworld.com/bi/bi_recommend_pop.php?url=" + Url
        //window.open('http://csp.cyworld.com/bi/bi_recommend_pop.php?url=' + Url + "&writer=잡코리아&title=" + encodeURIComponent(Title) + "&thumbnail=" + Thumbnail + "&summary=" + encodeURIComponent(Summary), 'recom_icon_pop', 'width=400,height=364,scrollbars=no,resizable=no');
        var farwindow = window.open('', '', 'width=400,height=364,scrollbars=no,resizable=no');

        if (farwindow != null) {
            if (farwindow.opener == null) {
                farwindow.opener = self;
            }
            farwindow.location.href = LinkPage;
        }
    }
    catch (e) {
        //alert(e.message);
    }
}


//SNS Shorten URL 포스팅수(버튼클릭수) 누적
var goPosting = function (Posting_Div) {
    $.ajax({
        type: "GET",
        url: "/Recruit/Sns_Posting",
        data : "Short_Div=" + sortdiv + "&Posting_Div=" + Posting_Div + "&Full_URL=" + escape(fullurl),
        cache: false,
        success: function (result) {            
        }
    });
}