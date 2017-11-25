---
layout: post
title: Bloc-Jams
thumbnail-path: "img/bloc-jams.png"
short-description: Bloc Jams is a Spotify-like app for playing your favorite songs online.

---

{:.center}
![]({{ site.baseurl }}/img/bloc-jams.png)

## Explanation

**Bloc-Jams** is an online ad-free music player. It is the first project I completed as a young developer, having only a six-month experience in coding. The project is part of my curriculum at Bloc. It

## Problem

The app is composed of a landing page where the features of the app are displayed, a collection page showing all albums available to play, and an album page displaying all songs of the album, that is the place where users can play, pause, skip or forward or song, and change its volume.

Bloc-Jams consists of two identical sub-projects, where the only difference between them is the language used; for the first one, I had to develop the app using JavaScript, and then refactor some of the code with jQuery. The second time, I had to implement features of the app using Angular. In both cases, the app had to be responsive.

## Solution

In this part, I will presents two code snippets, one for each sub project I did with each one presenting a different feature.


**Bloc-Jams using JavaScript & jQuery**

I will showcase and explain the feature that appears to me as the most difficult to implement. In the first case, it was implementing to the "next" button the behavior that allows users to go to the next song in the album.

{% highlight javascript %}
(1)
var nextSong = function() {
    var currentSongIndex = trackIndex(currentAlbum,
    currentSongFromAlbum);
    currentSongIndex++;
    (2)
    if (currentSongIndex >= currentAlbum.songs.length) {
        currentSongIndex = 0;
    }
    (3)
    var lastSongNumber = currentlyPlayingSongNumber;
    (4)
    setSong(currentSongIndex + 1);
    currentSoundFile.play();
    updateSeekBarWhileSongPlays();
    currentSongFromAlbum = currentAlbum.songs
    [currentSongIndex];

    updatePlayerBarSong();
    (5)
    var $nextSongNumberCell = getSongNumberCell
    (currentlyPlayingSongNumber);
    var $lastSongNumberCell = getSongNumberCell
    (lastSongNumber);

    $nextSongNumberCell.html(pauseButtonTemplate);
    $lastSongNumberCell.html(lastSongNumber);
};
{% endhighlight %}

>**(1)** Here, I named the function, hold in a variable the index of the song that was currently playing, and increment by one this index value.
**(2)** Then, I added a conditional statement to check if index value was above the total number of songs in the album, and if it is the case, then switch back to the first song of the album.
**(3)** Here, I hold the number of the song which was playing before users click on the next button.
**(4)** Once done, I used several methods, to first effictively play the next song and update the seek bar as the song plays.
**(5)** Finally, I used previously held values to replace the number of the song currently playing by a pause icon, and the pause icon of the previously playing song by its actual number.


**Bloc-Jams using Angular**

I will showcase and explain the feature that appears to me as the most interesting in terms of what I learned. In this case, I had to create a function that would take a song length in seconds as an input, and output it with a different format; for instance "133" has to become "2:13"  

{% highlight javascript %}
(1)
(function() {
     function timecode() {
         return function(seconds) {
            (2)
             var seconds = Number.parseFloat(seconds);
             (3)
             if (Number.isNaN(seconds)) {
                return '-:--';
             }
             (4)
             var wholeSeconds = Math.floor(seconds);
             var minutes = Math.floor(wholeSeconds / 60);
             var remainingSeconds = wholeSeconds % 60;

             var output = minutes + ':';
             (5)
             if (remainingSeconds < 10) {
                 output += '0';   
             }
             output += remainingSeconds;
             return output;
         };
     }
    (1)
     angular
         .module('blocJams')
         .filter('timecode', timecode);
 })();
{% endhighlight %}

>**(1)** Here, I declare the Angular module that will contain the timecode function, and added a closure at the end.
**(2)** I used the parseFloat method to get the seconds in number form.
**(3)** I added a conditional so that if the argument passed is not a number, the default format "-:--" get displayed.
**(4)** Then, I stored in the total number of minutes, and seconds of the song, and formated it as required.
**(5)** I added a conditional here as well so that if the remaining seconds of the song are under 10, a zero gets placed before the number. And finally, I returned the output.


## Conclusion

Being my first project using Javascript and Angular, I definitely learned a lot on the basis of these two programming languages. As a math geek, my main difficulties were not so much about finding out the math logic behind a certain behavior I wanted to implement, no matter how difficult, but rather putting all the logic together, and linking 
interrelated functions. This process is obviously difficult for young developers and especially with Angular, which I read about and was pleased to see that even developers with more experience still have difficulties to grasp its logic. After this project, I fell comfortable developing more complex apps.
