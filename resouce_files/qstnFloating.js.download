/*
 * 기업회원 홈 플로팅 버튼 동작 제어 스크립트
 * 대학, 대학교 유무, 로그인 유무, 정지 유무 확인
 */
$(document).ready(function () {
    $.ajax({
        type: "POST",
        url: "/User/Qstn/UserInfo",
        data: { cIdent: $("#hdnCIdent").val() },
        cache: false
    }).done(function (data) {
		if (typeof data !== 'undefined' && data !== '') {
			var $aCom = $('#dev_qna_company'); // 재직자 버튼
			var $aUniv = $('#dev_qna_univ');   // 동문 버튼
			var cHref = $aCom.attr('href');    // 재직자 버튼 링크 주소
			var cident = $("#hdnCIdent").val();
			var Gno = $("[name='Gno']").val();
			if (cident !== "" && typeof cident !== "undefined") {
				cident = cident.replace("-", "").replace("-", "").replace("-", "");
			}


			// 로그인
			if (data.login) {
				if (data.stop) {
					// 사용자 정지
					$aUniv.click(function (e) {
						e.preventDefault();
						alert('운영자에 의해 서비스 이용이 제한 되었습니다.\n서비스를 다시 이용하기 위해서는 고객센터로 요청 해주세요. (1588-9350)');
					});
				}
				else {
					//올바른 사용자
					if (data.resume === false) {
						// 이력서 없을 때
						$aUniv.click(function (e) {
							e.preventDefault();
							var goUrl = "";
							if (confirm('재직자에게 질문하기 위해서는 이력서를 먼저 등록해야 합니다. 지금 이력서를 작성해 볼까요?')) {
								goUrl = '/User/Resume/Write?qstn=all';
							} else {
								goUrl = '/User/Qstn/Index?MainType=3';
							}
							var openNewWindow = window.open("about:blank");
							openNewWindow.location.href = goUrl;

						});
					} else {
						//// 기업 정보 있을 때
						//if (data.cname !== '' && data.ccode !== 0) {
						//    cHref += '?type=2' + '&Qstn_Cname_Code=' + data.ccode + '&Qstn_Cname=' + data.cname;
						//    $aCom.attr('href', cHref);
						//}

						//// 이력서 있을 때
						//if (data.univ) {
						//    // 로그인, 대졸, 초대졸 입력, 사용자 비정지
						//    $aUniv.show();
						//}
						//else {
						//    // 대졸, 초대졸 미입력
						//}
						$aUniv.click(function (e) {
							e.preventDefault();
							//window.location = '/User/Qstn/QstnWrite?Biz_No=' + cident;
							var openNewWindow = window.open("about:blank");
							openNewWindow.location.href = '/User/Qstn/QstnWrite?Biz_No=' + cident + '&gno=' + Gno;

						});

					}
				}
			} else {
				// 비로그인
				var rtnMsg = "개인회원 로그인 후 이용할 수 있습니다. 지금 로그인하고 질문할까요?";
				var rtnUrl = "/Login/Login_Tot.asp?rDBName=GG&ignoreSession=1&re_url=/User/Qstn/Index";
				//$aUniv.add($aUniv).click(function (e) {
				$aUniv.click(function (e) {
					e.preventDefault();

					if (confirm(rtnMsg)) {
						//location.href = rtnUrl;
						var openNewWindow = window.open("about:blank");
						openNewWindow.location.href = rtnUrl;
					}
				});
			}
		} else {
			var $aUniv = $('#dev_qna_univ');   // 동문 버튼
			var rtnUrl = "/Login/Login_Tot.asp?rDBName=GG&ignoreSession=1&re_url=" + escape(location.href);
			$aUniv.click(function (e) {
				e.preventDefault();
				location.href = rtnUrl;
				//var openNewWindow = window.open("about:blank");
				//openNewWindow.location.href = rtnUrl;
			});
		}
    });
});