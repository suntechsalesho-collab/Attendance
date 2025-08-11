<!DOCTYPE html>
<html>
<head>
  <title>Attendance (Location Capture)</title>
  <script>
    function getLocation() {
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(sendToForm, showError);
      } else {
        alert("Geolocation is not supported by this browser.");
      }
    }

    function sendToForm(position) {
      var lat = position.coords.latitude;
      var lon = position.coords.longitude;

      var formURL = "https://docs.google.com/forms/d/e/1FAIpQLSerP1oruGjNKnptVAMpiWUFd3Ez9FFS_3SL7Ab5_jKFPKjTqg/viewform?usp=pp_url" +
        "&entry.1819631931=Name" +
        "&entry.1614523089=In & Out" +
        "&entry.936853258=Designation" +
        "&entry.1821367526=ID card no." +
        "&entry.17464104=" + encodeURIComponent(lat) +
        "&entry.544060370=" + encodeURIComponent(lon);

      window.location.href = formURL;
    }

    function showError(error) {
      switch (error.code) {
        case error.PERMISSION_DENIED:
          alert("Location permission denied. Form cannot be accessed.");
          break;
        case error.POSITION_UNAVAILABLE:
          alert("Location information is unavailable.");
          break;
        case error.TIMEOUT:
          alert("Request to get location timed out.");
          break;
        default:
          alert("An unknown error occurred.");
      }
    }
  </script>
</head>
<body onload="getLocation()">
  <h2>Please wait... capturing your location.</h2>
</body>
</html>
