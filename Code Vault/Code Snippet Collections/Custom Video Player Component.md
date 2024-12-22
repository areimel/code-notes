
## HTML/JSX (Structure)
```jsx
/*===== Components =====*/
import React from "react"
import Link from 'next/link'


//import Button1 from '@components/Button1'
import ContentScrollContainer from '@components/ContentScrollContainer'
import { FaPlay } from "react-icons/fa6";
import { FaPause } from "react-icons/fa6";

/*===== Styles =====*/
import componentStyles from './styles.module.scss'


export default function SubSliderType2({ 
  //Props
  videoPlayerID, webmSrc, mp4Src, errorMessage, width,
}) {

  //console.log(author);

  return (
    <div 
      className={componentStyles.CustomVideoPlayer+ " CustomVideoPlayer"}
      id={videoPlayerID ? videoPlayerID : "warning-must-have-unique-id"}
      data-state="initial"
    >
      {/* Big Play Button / Initial Play Button */}
      <div className={`${componentStyles.bigPlayButton} bigPlayButton`}><FaPlay/></div>
      
      {/* HTML5 Video Element - actual 'player' element */}
      <video 
        //controls
        //playsInline
        poster=''
        width={width ? width : "250"}
      >
        {webmSrc && 
          <source src={webmSrc} type="video/webm" />
        }
        {mp4Src && 
          <source src={mp4Src} type="video/mp4" />
        }

        <div>
          <p>Video Error</p>
          <br/>
          {errorMessage ? errorMessage :
            <p>Either the your browser can't play the video, or the video link doesn't exist.</p>
          }
        </div>

      </video>
      
      {/* Control Bar */}
      <div className={`${componentStyles.controls} controls`}>
        <button 
          className={`${componentStyles.play} play`} 
          data-icon="P" 
          aria-label="play pause toggle"
        >
          <span className={`${componentStyles.playIcon}`}><FaPlay /></span>
          <span className={`${componentStyles.pauseIcon}`}><FaPause /></span>
        </button>
        <div className={`${componentStyles.timerClock} timerClock`} aria-label="timer">00:00</div>
        {/* <button className="stop" data-icon="S" aria-label="stop"></button> */}
        <div className={`${componentStyles.timer} timer`}>
          <div></div>
        </div>
        
      </div>

    </div>
    
  )
}
```

## CSS (Style)
```scss
.CustomVideoPlayer{
    $controlsFadeTiming: 0.25s;
    $controlsHeight: 5vh;
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100%;
    video{
        z-index: 5;
        width: 100%;
        height: 100%;
    }
    .bigPlayButton{
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%,-50%);
        z-index: 10;
        width: 5vw;
        height: 5vw;
        border-radius: 100%;
        border: solid 2px $white;
        background-color: $darkBlue;
        font-size: 1.25rem;
        padding-left: 1%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        cursor: pointer;
        opacity: 0;
        pointer-events: none;
        transition: $controlsFadeTiming;

        svg{
            width: 80%;
        }
    }
    .controls{
        //visibility: hidden;
        opacity: 0;
        pointer-events: none;
        width: 65%;
        height: $controlsHeight;
        //border-radius: 10px;
        position: absolute;
        z-index: 6;
        bottom: 20px;
        left: 50%;
        transform: translate(-50%, 0);
        background-color: $black;
        //box-shadow: 3px 3px 5px black;
        transition: 0.5s;
        display: flex;

        .play{
            position: relative;
            width: $controlsHeight;
            border: solid 2px $white;
            background-color: $white;
            color: $black;
            .playIcon,
            .pauseIcon{
                opacity: 0;
                position: absolute;
                left: 50%;
                top: 50%;
                transform: translate(-50%, -50%);
            }
        }

        .timer {
            line-height: $controlsHeight;
            
            flex: 5;
            position: relative;
        }

        .timer div {
            position: absolute;
            background-color: $white;
            left: 0;
            top: 0;
            width: 0;
            height: $controlsHeight;
            //transition: 0.25s;
            //transition-timing-function: linear;
            //border-radius: 10px;
            z-index: 2;
        }

        .timerClock {
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 3;
            left: 0px;
            width: calc($controlsHeight + 20px);
            font-size: 0.5rem;
            font-family: monospace;
            //text-shadow: 1px 1px 0px black;
            color: $black;
            background-color: $white;
            border-left: solid 1px $black;
            border-right: solid 1px $black;
            //background-color: $black;
        }
    }
    
     

    //Action States - show/hide sub-elements
    &:hover, &:focus-within{
        .controls {
            opacity: 1;
            pointer-events: auto;
            //visibility: visible;
        }
    }

    &[data-state="stopped"],
    &[data-state="initial"]{
        .bigPlayButton{
            opacity: 1;
            pointer-events: auto;
        }
        .play{
            .playIcon{
                opacity: 1;
            }
            .pauseIcon{
                opacity: 0;
            }
        }
    }
    &[data-state="playing"]{
        .play{
            .playIcon{
                opacity: 0;
            }
            .pauseIcon{
                opacity: 1;
            }
        }
        .controls {
            opacity: 0.25;
            pointer-events: auto;
            //visibility: visible;
        }
        &:hover, &:focus-within{
            .controls {
                opacity: 1;
                pointer-events: auto;
                //visibility: visible;
            }
        }
    }
    &[data-state="paused"]{
        .play{
            .playIcon{
                opacity: 1;
            }
            .pauseIcon{
                opacity: 0;
            }
        }
    }
}
```

## JS (Controls)
```jsx
<!-- Code Goes Here -->
```

