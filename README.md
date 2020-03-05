# FrameRequest



## Description

A Typescript/Javascript library for iframe requests/responses

## Getting Started

### Installing

```
npm i frame-request
```

## Usage

In your parent window javascript file simply put:

```
import {FrameRequest} from 'frame-request';

const channel = new FrameRequest('Some Channel Name', {
        // Define what to do with requests 
        world: ({payload}) => {
            console.log(payload); // 
        }
}, "my-iframe-selector");

channel
    .request('helloRequest', {myData: 'hello'})
    .then((res) => {
        console.log(res); // {world: 'world'}
    });
```

In your iframe's javascript file put:

```
import { FrameRequest } from "frame-request";

const channel = new FrameRequest('Some Channel Name', {
    helloRequest: ({payload, reply}) => {
        console.log(payload); // {myData: 'hello'}
        reply({
            world: 'world'
        });
    }
}); 
```

## Authors

Guy Golan - [@GuyGolan](https://www.linkedin.com/in/guy-golan-351312a6)


## Version History

* 1.0.11 added README.md and refactored name to FrameRequest
* 1.0.10
    * Various bug fixes and optimizations
    * See [commit change](https://github.com/guygolanIL/FrameRequest/commits/master)