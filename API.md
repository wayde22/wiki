```js myVar = () => {
  fetch('address')
    .then(response => response.json())
    .then(jason => console.log(json.quote))
  }

fetch will go get the data you are wanting to retrieve that is called a promise,
  .then will wait for the data before it goes on to the next thing


 asyncAwaitFetch = async () => {
  const response = await fetch('https://api.spacexdata.com/v3/ships/GOQUEST');
  const json = await response.json();
  this.setState({ asyncAwaitFetch: json.ship_name });
  };
  
  asyncAwaitFetch = async () => {
    const response = await fetch('https://api.spacexdata.com/v3/roadster');
    const json = await response.json();
    this.setState({ myThingInState: json.stuff });
  };```
