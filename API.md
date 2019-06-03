myVar = () => {
  fetch('address')
    .then(response => response.json())
    .then(jason => console.log(json.quote))
  }

fetch will go get the data you are wanting to retrieve that is called a promise,
  .then will wait for the data before it goes on to the next thing
