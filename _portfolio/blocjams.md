---
layout: post
title: BlocJams
feature-img: "img/sample_feature_img.png"
thumbnail-path: "https://d13yacurqjgara.cloudfront.net/users/3217/screenshots/2030966/blocjams_1x.png"
short-description: BlocJams with AngularJS

---
Summary:
A music playing website made as a learning project for Angular JS. Designed to hold multiple albums, play individual songs, and have a functioning overlay with seek and voulme bars.

Explanation:
The site was created to learn the basics of AngularJS and was written with the guidance of Bloc

Examples:

* In order to kep track of the user moving the track bar for songs and volume, I used the bind method from jQuery and angular's $apply method.
{% highlight javascript %}
scope.trackThumb = function() {
    $document.bind('mousemove.thumb', function(event) {
        var percent = calculatePercent(seekBar, event);
        scope.$apply(function() {
           scope.value = percent * scope.max;
           notifyOnChange(scope.value);
        });
    });
 
    $document.bind('mouseup.thumb', function() {
    $document.unbind('mousemove.thumb');
    $document.unbind('mouseup.thumb');
});
{% endhighlight %}

* I was tasked with making a function to attach to the skip next button so when pressed it would begin playing the following song. When it is pressed and the album is on its last track it'll restart with the first song on the album

{% highlight javascript %}

SongPlayer.next = function() {
    var currentSongIndex = getSongIndex(SongPlayer.currentSong);
    currentSongIndex++;

    if (currentSongIndex > currentAlbum.songs.length) {
        stopSong();
    } else {
        var song = currentAlbum.songs[currentSongIndex];
        setSong(song);
        playSong(song);
    }

};

{% endhighlight %}

Conclusion:
The project taught me how to use Angular's Services, Controllers, Directives, Filters, and how to connect them all together.