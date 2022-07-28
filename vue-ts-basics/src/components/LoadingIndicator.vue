<script src="https://cdnjs.cloudflare.com/ajax/libs/react/15.4.1/react.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/react/15.4.1/react-dom.js"></script>

<div id="app"></div>

<div class="loader"></div>

const loader = document.querySelector('.loader');

// if you want to show the loader when React loads data again
const showLoader = () => loader.classList.remove('loader--hide');

const hideLoader = () => loader.classList.add('loader--hide');

class App extends React.Component {
  componentDidMount() {
    this.props.hideLoader();
  }
  
  render() {   
    return (
      <div>I'm the app</div>
    ); 
  }
}

// the setTimeout simulates the time it takes react to load, and is not part of the solution
setTimeout(() => 
  // the show/hide functions are passed as props
  ReactDOM.render(
    <App
      hideLoader={hideLoader}
      showLoader={showLoader} 
      />,
    document.getElementById('app')
  )
, 1000);



//Another code snippet
constructor() {
    this.state = { isLoading: true }
}

componentDidMount() {
    this.setState({isLoading: false})
}

render() {
    return(
        this.state.isLoading ? *showLoadingScreen* : *yourPage()*
    )
}