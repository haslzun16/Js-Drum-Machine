const sounds = [
  {
    key: "Q",
    mp3: "https://s3.amazonaws.com/freecodecamp/drums/Heater-1.mp3",
    id: "Heater-1"
  },
  {
    key: "W",
    mp3: "https://s3.amazonaws.com/freecodecamp/drums/Heater-2.mp3",
    id: "Heater-2"
  },
  {
    key: "E",
    mp3: "https://s3.amazonaws.com/freecodecamp/drums/Heater-3.mp3",
    id: "Heater-3"
  },
  {
    key: "A",
    mp3: "https://s3.amazonaws.com/freecodecamp/drums/Heater-4_1.mp3",
    id: "Heater-4"
  },
  {
    key: "S",
    mp3: "https://s3.amazonaws.com/freecodecamp/drums/Heater-6.mp3",
    id: "Heater-6"
  },
  {
    key: "D",
    mp3: "https://s3.amazonaws.com/freecodecamp/drums/Dsc_Oh.mp3",
    id: "Dsc_Oh"
  },
  {
    key: "Z",
    mp3: "https://s3.amazonaws.com/freecodecamp/drums/Kick_n_Hat.mp3",
    id: "Kick_n_Hat"
  },
  {
    key: "X",
    mp3: "https://s3.amazonaws.com/freecodecamp/drums/RP4_KICK_1.mp3",
    id: "RP4_KICK_1"
  },
  {
    key: "C",
    mp3: "https://s3.amazonaws.com/freecodecamp/drums/Cev_H2.mp3",
    id: "Cev_H2"
  }
];

const App = () => (
  <div className="container">
    <div className="display" id="display">
      <h1>Play a sound</h1>
      {sounds.map((sound, idx) => (
        <DrumPad
          text={sound.key}
          keys={idx}
          audio={sound.mp3}
          name={sound.id}
        />
      ))}
    </div>
  </div>
);

class DrumPad extends React.Component {
  constructor(props) {
    super(props);

    this.audio = React.createRef();
  }

  componentDidMount() {
    this.audio.current.addEventListener("ended", (e) => {
      const parent = e.target.parentNode;
      parent.classList.remove("active");
    });
  }

  playSound = () => {
    this.audio.current.play();

    const id = this.audio.current.id;

    const parent = this.audio.current.parentNode;
    parent.classList.add("active");

    const display = parent.parentNode;
    display.querySelector("h1").innerText = id + " is playing";
  };

  render() {
    const { text, audio, id } = this.props;

    return (
      <div className="drum-pad" onClick={this.playSound} id={"drum-${text}"}>
        {text}
        <audio ref={this.audio} src={audio} className="clip" id={text} />
      </div>
    );
  }
}

document.addEventListener("keydown", (e) => {
  const id = e.key.toUpperCase();
  const audio = document.getElementById(id);

  if (audio) {
    audio.currentTime = 0;
    const parent = audio.parentNode;
    parent.classList.add("active");

    const display = parent.parentNode;
    display.querySelector("h1").innerText = audio.id + " is playing";
    audio.play();
  }
});

ReactDOM.render(<App />, document.getElementById("drum-machine"));
