media.play
==========

오디오 파일을 재생하는 것을 시작하거나 재개한다.

    media.play();


설명
-----------

`media.play` 함수는 오디오 파일을 재생하는 것을 시작하거나 재개하는 동기화 함수이다.  

지원하는 플랫폼
-------------------

- Android
- iOS
    
빠른 예제
-------------

    // 오디오을 재생한다.
    //
    function playAudio(url) {
        // url의 오디오 파일을 재생한다.
        var my_media = new Media(url,
            // 성공 콜백 
            function() {
                console.log("playAudio():Audio Success");
            },
            // 실패 콜백
            function(err) {
                console.log("playAudio():Audio Error: "+err);
        });

        // 오디오를 재생한다.
        my_media.play();
    }


전체 예제
------------

        <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
                              "http://www.w3.org/TR/html4/strict.dtd">
        <html>
          <head>
            <title>Media Example</title>
        
            <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
            <script type="text/javascript" charset="utf-8">
        
            // PhoneGap이 로드되기를 기다린다
            //
            document.addEventListener("deviceready", onDeviceReady, false);
        
            // PhoneGap이 준비되면 호출된다
            //
            function onDeviceReady() {
                playAudio("http://audio.ibeat.org/content/p1rj1s/p1rj1s_-_rockGuitar.mp3");
            }
        
            // Audio player
            //
            var my_media = null;
            var mediaTimer = null;
        
            // 오디오를 재생한다.
            //
            function playAudio(src) {
            	if (my_media == null) {
                	// src로부터 Media 객체를 생성한다.
                	my_media = new Media(src, onSuccess, onError);
            	} // 그렇지 않으면 현재 오디오를 재생한다.
                // 오디오를 재생한다.
                my_media.play();
        
                // 매 초마다 my_media 위치를 갱신한다.
                if (mediaTimer == null) {
                    mediaTimer = setInterval(function() {
                        // my_media 위치를 얻는다.
                        my_media.getCurrentPosition(
                            // 성공 콜백 
                            function(position) {
                                if (position > -1) {
                                    setAudioPosition((position) + " sec");
                                }
                            },
                            // 에러 콜백
                            function(e) {
                                console.log("Error getting pos=" + e);
                                setAudioPosition("Error: " + e);
                            }
                        );
                    }, 1000);
                }
            }
        
            // 오디오를 일시정지한다.
            // 
            function pauseAudio() {
                if (my_media) {
                    my_media.pause();
                }
            }
        
            // 오디오를 멈춘다.
            // 
            function stopAudio() {
                if (my_media) {
                    my_media.stop();
                }
                clearInterval(mediaTimer);
                mediaTimer = null;
            }
        
            // onSuccess 콜백
            //
            function onSuccess() {
                console.log("playAudio():Audio Success");
            }
        
            // onError 콜백
            //
            function onError(error) {
                alert('code: '    + error.code    + '\n' + 
                      'message: ' + error.message + '\n');
            }
        
            // 오디오 위치를 설정한다.
            // 
            function setAudioPosition(position) {
                document.getElementById('audio_position').innerHTML = position;
            }
        
            </script>
          </head>
          <body>
            <a href="#" class="btn large" onclick="playAudio('http://audio.ibeat.org/content/p1rj1s/p1rj1s_-_rockGuitar.mp3');">Play Audio</a>
            <a href="#" class="btn large" onclick="pauseAudio();">Pause Playing Audio</a>
            <a href="#" class="btn large" onclick="stopAudio();">Stop Playing Audio</a>
            <p id="audio_position"></p>
          </body>
        </html>
