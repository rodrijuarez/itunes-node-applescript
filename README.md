# itunes-node-applescript
Control Spotify on Mac OSX with NodeJS and AppleScript.

## Installation

```
$ npm install itunes-node-applescript
```

## Running unit tests

```
$ npm test
```

## API

### playTrack(uri, callback)

Play a track with Spotify URI `uri`.

```javascript
var spotify = require('itunes-node-applescript');

spotify.playTrack('spotify:track:3AhXZa8sUQht0UEdBJgpGc', function(){
    // track is playing
});
```

### playTrackInContext(uri, contextUri, callback)

Play a track in context of for example an album.

```javascript
var spotify = require('itunes-node-applescript');

spotify.playTrackInContext('spotify:track:0R8P9KfGJCDULmlEoBagcO', 'spotify:album:6ZG5lRT77aJ3btmArcykra', function(){
    // Track is playing in context of an album
});
```

### getTrack(callback)

Get the current track. `callback` is called with the current track as second argument.

```javascript
var spotify = require('itunes-node-applescript');

spotify.getTrack(function(err, track){

    /*
    track = {
        artist: 'Bob Dylan',
        album: 'Highway 61 Revisited',
        disc_number: 1,
        duration: 370,
        played count: 0,
        track_number: 1,
        starred: false,
        popularity: 71,
        id: 'spotify:track:3AhXZa8sUQht0UEdBJgpGc',
        name: 'Like A Rolling Stone',
        album_artist: 'Bob Dylan',
        spotify_url: 'spotify:track:3AhXZa8sUQht0UEdBJgpGc' }
    }
    */

});
```

### getState(callback)

Get player state.

```javascript
var spotify = require('itunes-node-applescript');

spotify.getState(function(err, state){
    /*
    state = {
        volume: 99,
        position: 232,
        state: 'playing'
    }
    */
});
```

### jumpTo(second, callback)

Jump to a specific second of the current song.

```javascript
var spotify = require('itunes-node-applescript');

spotify.jumpTo(15, function() {
    console.log('Jumped 15th second of the song');
});
```

### play(callback)

Resume playing current track.

### pause(callback)

Pause playing track.

### playPause(callback)

Toggle play.

### next(callback)

Play next track.

### previous(callback)

Play previous track.

### volumeUp(callback)

Turn volume up.

### volumeDown(callback)

Turn volume down.

### setVolume(volume, callback)

Sets the volume.

```javascript
var spotify = require('itunes-node-applescript');

spotify.setVolume(42, function() {
    spotify.getState(function(err, state) {
        console.log(state.volume);
    });
});
```

### muteVolume(callback)

Reduces audio to 0, saving the previous volume.

### unmuteVolume(callback)

Returns audio to original volume.

### isRunning(callback)

Check if Spotify is running.

```javascript
var spotify = require('itunes-node-applescript');

spotify.isRunning(function(err, isRunning){
    console.log(isRunning); // true
});
```

## Contributors

* [Robin Mehner](https://github.com/rmehner)
* [Thorsten Ball](https://github.com/mrnugget)
* [Paul Marbach](https://github.com/fastfrwrd)

## License

[MIT](LICENSE)
