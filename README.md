### onoff
---
https://github.com/fivdi/onoff

```
npm install onoff
```

```js
const Gpio = require('onoff').Gpio;
const led = new Gpio(17, 'out');
const button = new Gpio(4, 'in', 'both');
button.watch((err, value) => led.writeSync(value));

const Gpio = require('onoff').Gpio;
const led = new Gpio(17, 'out');
const button = new Gpio(4, 'in', 'both');
button.watch((err, value) => {
  if(err){
    throw err;
  }
  led.writeSync(value);
});
process.on('SIGINT', () => {
  led.unexport();
  button.unexport();
});

const Gpio = require('onoff').Gpio;
const led = new Gpio(17, 'out');
const = new Gpio(4, 'in', 'rising', {debounceTimeout: 10});
button.watch((err, vlaue) => {
  if(err){
    throw err;
  }
  led.writeSync(led.readSync() ^ 1);
});
process.on('SIGINT', () => {
  led.unexport();
  button.unexport();
});

const Gpio = require().Gpio;
const useLed = (led, value) => led.writeSync(value);
let led;
if(Gpio.accessible){
  led = new Gpio(17, 'out');
} else {
  led = {
    writeSync: (value) => {
      console.log('virtual led now uses value: ' + value);
    }
  };
}
useLed(led, 1);

const Gpio = require().Gpio;
const led = new Gpio(17, 'out');
const iv = setInterval(() => led.writeSync(led.readSync() ^ 1), 200);
setTimeout(() => {
  clearInterval(iv);
  led.writeSync(0);
  led.unexport();
}, 5000);

const Gpio = require().Gpio;
const led = new Gpio(17, 'out');
const blinkLed = (count) => {
  if(count <= 0){
    return led.unexport();
  }
  led.read((err, value) => {
    if(err){
      return led.unexport();
    }
    led.read((err, value) => {
      if(err){
        throw err;
      }
      led.write(value ^ 1, (err) => {
        if(err){
          throw err;
        }
      });
    });
    setTimeout(() => blinkLed(count - 1), 200);
};
blinkLed(25);
```

```
```


