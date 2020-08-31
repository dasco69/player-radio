<template>
    <div style="position:relative">
        
        <div id="player-radio">
            <img src="" alt="album" id="img-album">
            <span id="info-music">
                <h2 id="artist">Artiste</h2>
                <h4 id="title-music">Title of music</h4>
            </span>
            <!-- serateur vertical -->
            <hr>
            <div class="" id="option-player">
                <!--Play method-->
                <span 
                    @click="play"
                    >
                    <!--Play icon-->
                    <svg v-if="playerOn" id="play" x="0px" y="0px" viewBox="0 0 163.861 163.861" style="enable-background:new 0 0 163.861 163.861;" xml:space="preserve">
                        <g>
                            <path d="M34.857,3.613C20.084-4.861,8.107,2.081,8.107,19.106v125.637c0,17.042,11.977,23.975,26.75,15.509L144.67,97.275c14.778-8.477,14.778-22.211,0-30.686L34.857,3.613z"/>
                        </g>
                    </svg>
                    <!--Pause icon-->
                    <svg v-else id="pause" x="0px" y="0px" viewBox="0 0 45.975 45.975" style="enable-background:new 0 0 45.975 45.975;" xml:space="preserve">
                        <g>
                            <path d="M13.987,0c-2.762,0-5,2.239-5,5v35.975c0,2.763,2.238,5,5,5s5-2.238,5-5V5C18.987,2.238,16.75,0,13.987,0z"/>
                            <path d="M31.987,0c-2.762,0-5,2.239-5,5v35.975c0,2.762,2.238,5,5,5s5-2.238,5-5V5C36.987,2.239,34.749,0,31.987,0z"/>
                        </g>
                    </svg>
                </span>
                <!-- Volume -->
                <span 
                    @click="volume"
                    :class="{'levelEnable' : level}">
                    <!--show if level it's false, and when you click inside show range volume-->
                    <svg v-if="!level" id="volume" x="0px" y="0px" viewBox="0 0 480.1 480.1" style="enable-background:new 0 0 480.1 480.1;" xml:space="preserve">
                        <g>
                            <path d="M240.1,197.8c-28.9,0-56,11.3-76.5,31.7c-20.4,20.4-31.7,47.6-31.7,76.5s11.2,56,31.7,76.5s47.6,31.7,76.5,31.7
                                s56-11.2,76.5-31.7s31.7-47.6,31.7-76.5s-11.2-56-31.7-76.5C296.1,209.1,269,197.8,240.1,197.8z M299.6,365.5
                                c-15.9,15.9-37,24.6-59.5,24.6s-43.6-8.8-59.5-24.6c-15.9-15.9-24.6-37-24.6-59.5s8.8-43.6,24.6-59.5c15.9-15.9,37-24.6,59.5-24.6
                                s43.6,8.8,59.5,24.6c15.9,15.9,24.6,37,24.6,59.5C324.2,328.4,315.5,349.6,299.6,365.5z"/>
                            <path d="M282,261.3c-5.9-4.6-14.4-3.6-19,2.3c-4.3,5.4-3.7,13.2,1.1,17.9c0.4,0.4,0.8,0.8,1.2,1.1l0,0c5.9,4.6,14.4,3.6,19.1-2.3
                                C288.9,274.5,287.9,265.9,282,261.3z"/>
                            <path d="M12,293.9c-3.2,0-6.3,1.3-8.5,3.5S0,302.7,0,305.9s1.3,6.3,3.5,8.5s5.3,3.5,8.5,3.5s6.3-1.3,8.5-3.5s3.5-5.3,3.5-8.5
                                s-1.3-6.3-3.5-8.5C18.3,295.2,15.2,293.9,12,293.9z"/>
                            <path d="M373.4,106.3c-5.5-3.7-13-2.2-16.7,3.3s-2.2,13,3.3,16.6c2.1,1.4,4.4,2,6.7,2c3.9,0,7.7-1.9,10-5.3
                                C380.4,117.4,378.9,109.9,373.4,106.3z"/>
                            <path d="M322.7,106.2L322.7,106.2c1.5,0.6,3.1,0.9,4.6,0.9c4.7,0,9.2-2.8,11.1-7.4c2.5-6.1-0.4-13.1-6.5-15.7
                                c-6.1-2.5-13.1,0.4-15.7,6.5C313.7,96.7,316.6,103.7,322.7,106.2z"/>
                            <path d="M282.2,94c0.8,0.2,1.6,0.2,2.3,0.2c5.6,0,10.6-4,11.8-9.7c1.3-6.5-3-12.8-9.5-14.1c-6.5-1.3-12.8,2.9-14.1,9.5
                                C271.4,86.4,275.7,92.7,282.2,94z"/>
                            <path d="M392.8,136.1c-4.7,4.7-4.7,12.3,0,17c2.3,2.3,5.4,3.5,8.5,3.5s6.1-1.2,8.5-3.5c4.7-4.7,4.7-12.3,0-17
                                C405,131.4,397.4,131.4,392.8,136.1z"/>
                            <path d="M240,89.9c6.6,0,12-5.4,12-12s-5.4-12-12-12s-12,5.4-12,12S233.4,89.9,240,89.9z"/>
                            <path d="M33.9,207.6c-6.1-2.5-13.1,0.4-15.7,6.5c-2.5,6.1,0.4,13.1,6.5,15.7c1.5,0.6,3.1,0.9,4.6,0.9c4.7,0,9.2-2.8,11.1-7.4
                                C43,217.1,40.1,210.1,33.9,207.6z"/>
                            <path d="M18.7,249.7c-6.5-1.3-12.8,2.9-14.1,9.4c-1.3,6.5,2.9,12.8,9.4,14.1c0.8,0.2,1.6,0.2,2.3,0.2c5.6,0,10.6-4,11.8-9.7
                                C29.4,257.3,25.2,251,18.7,249.7z"/>
                            <path d="M152.8,107.2c1.5,0,3.1-0.3,4.6-0.9c6.1-2.5,9-9.6,6.5-15.7s-9.6-9-15.7-6.5c-6.1,2.5-9,9.6-6.5,15.7
                                C143.6,104.4,148,107.2,152.8,107.2z"/>
                            <path d="M461.9,213.9c-2.5-6.1-9.6-9-15.7-6.5c-6.1,2.6-9,9.6-6.5,15.7c1.9,4.6,6.4,7.4,11.1,7.4c1.5,0,3.1-0.3,4.6-0.9
                                C461.5,227,464.4,220,461.9,213.9z"/>
                            <path d="M439.6,172.4c-3.7-5.5-11.1-7-16.7-3.3c-5.5,3.7-7,11.1-3.3,16.6c2.3,3.5,6.1,5.3,10,5.3c2.3,0,4.6-0.7,6.7-2
                                C441.8,185.4,443.3,177.9,439.6,172.4z"/>
                            <path d="M466.1,273c6.5-1.3,10.7-7.6,9.4-14.1c-1.3-6.5-7.6-10.7-14.1-9.4c-6.5,1.3-10.7,7.6-9.4,14.1c1.1,5.7,6.1,9.7,11.8,9.7
                                C464.5,273.3,465.3,273.2,466.1,273z"/>
                            <path d="M195.5,94.3c0.8,0,1.6-0.1,2.4-0.2c6.5-1.3,10.7-7.6,9.4-14.1s-7.6-10.7-14.1-9.4s-10.7,7.6-9.4,14.1
                                C184.9,90.3,189.9,94.3,195.5,94.3z"/>
                            <path d="M106.7,106.4c-5.5,3.7-7,11.1-3.3,16.6c2.3,3.5,6.1,5.3,10,5.3c2.3,0,4.6-0.7,6.7-2c5.5-3.7,7-11.1,3.3-16.6
                                C119.6,104.1,112.2,102.7,106.7,106.4z"/>
                            <path d="M57.1,169.3c-5.5-3.7-13-2.2-16.6,3.3c-3.7,5.5-2.2,13,3.3,16.6c2.1,1.4,4.4,2,6.7,2c3.9,0,7.7-1.9,10-5.3
                                C64.1,180.4,62.6,173,57.1,169.3z"/>
                            <path d="M70.4,136.2c-4.7,4.7-4.7,12.3,0,17c2.3,2.4,5.4,3.5,8.5,3.5s6.1-1.2,8.5-3.5c4.7-4.7,4.7-12.3,0-17
                                C82.6,131.5,75,131.5,70.4,136.2z"/>
                            <path d="M476.6,297.5c-2.2-2.2-5.3-3.5-8.5-3.5s-6.3,1.3-8.5,3.5s-3.5,5.3-3.5,8.5s1.3,6.3,3.5,8.5s5.3,3.5,8.5,3.5
                                s6.3-1.3,8.5-3.5s3.5-5.3,3.5-8.5S478.9,299.7,476.6,297.5z"/>
                        </g>
                    </svg>
                     <span v-else>
                         <input v-model="volRange" type="range" id="vol-range" name="vol" min="0" max="50" step="1" value="25">
                        <label for="vol-range">{{volRange}}</label>
                    </span> 
                    
                </span>
                <!--Menu Playlist -->
                <span @click="playlist">
                    <svg id="menu-playlist" x="0px" y="0px" viewBox="0 0 384.97 384.97" style="enable-background:new 0 0 384.97 384.97;" xml:space="preserve">
                        <g id="Menu_1_">
                            <path d="M12.03,120.303h360.909c6.641,0,12.03-5.39,12.03-12.03c0-6.641-5.39-12.03-12.03-12.03H12.03
                                c-6.641,0-12.03,5.39-12.03,12.03C0,114.913,5.39,120.303,12.03,120.303z"/>
                            <path d="M372.939,180.455H12.03c-6.641,0-12.03,5.39-12.03,12.03s5.39,12.03,12.03,12.03h360.909c6.641,0,12.03-5.39,12.03-12.03
                                S379.58,180.455,372.939,180.455z"/>
                            <path d="M372.939,264.667H132.333c-6.641,0-12.03,5.39-12.03,12.03c0,6.641,5.39,12.03,12.03,12.03h240.606
                                c6.641,0,12.03-5.39,12.03-12.03C384.97,270.056,379.58,264.667,372.939,264.667z"/>
                        </g>
                    </svg>
                </span>
                <audio  autoplay>
                    <source :src="urlRadio" type="audio/mpeg">
                </audio>
            </div>
            
        </div>

    </div>
</template>

<script>
    export default {
        name: 'Player',
        data() {
            return {
                musicInfo:  [
                    {
                        titleOfMusic : '',
                        artist: '',
                        cover: ''
                    }
                ],
                urlRadio : "http://82.165.206.27:8000/mazette",
                playerOn: false,
                level : false,
                volRange: 25
            }
        },
        methods: {
            
            play() {
                this.playerOn = !this.playerOn
                
                /**
                 * source: https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement
                 */

                //We cacth HTML element audio
                let audio = document.querySelector('audio')

                if(!this.playerOn) {
                    //Every time we load the flux for direct
                    audio.load()
                    //After have load we play
                    audio.play()
                } else {
                    // Just for stop the flux
                    audio.pause()
                }
                
            },
            volume(el) {
                //  <input type="range" id="vol" name="vol" min="0" max="50">
                this.level = !this.level
                console.log(this.volRange)     

            },
            playlist() {
                return console.log('Playlost')
            }
        },
        mounted () {
            //https://developers.google.com/web/updates/2017/09/autoplay-policy-changes
            const audio = document.querySelector('audio')
            const promise = audio.play()

            if (promise !== undefined) {
                promise.then(_ => {
                    console.lg('autoplay marche')
                    // Autoplay started!
                    audio.autoplay = true
                    audio.load()
                }).catch(error => {
                    console.log('autoplay marche pas')
                    // Autoplay was prevented.
                    // Show a "Play" button so that user can start playback.
                    this.play()
                });
            }
        },
    }
</script>

<style lang="scss" scoped>
#player-radio {
    display: inline-flex;
    position: absolute;
    right: 0;
    width: 32%;
    height: 4em;
    background: #fff;
    color: #aaa;
    :only-child {
        margin-left: 2em;
    }
    img {
        width: 4em;
        height: auto;
        background: red;

    }
    #info-music {
        width: 5em;
        margin: 0 .5em;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        h2 {
             font-size: 1em;
             margin: 0;
        }
        h4 {
            font-size: .8em;
            font-weight: lighter;
        }
    }
    hr {
        margin: 0!important
    }
    #option-player {
        display: flex;
        align-items: center;
        #play, #pause, #volume , #menu-playlist{
            width: 2em;
            height: 2em;
            fill: #1a1a1a;
        }
        .levelEnable {
            width: 4em;
            #vol-range {
                transform: rotate(-90deg);
                transform-origin: 75px 75px;
            }
        }
        

    }
    
}

</style>