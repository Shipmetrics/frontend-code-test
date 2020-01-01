# js-test-project

This project is supposed to submit Tasks (simple objects) to a server where they eventually get "processed". Multiple browser-clients should be able to queue tasks simultaneously. All clients must receive updates in real-time.

## Structure

- Both projects (server and frontend) use the same package.json. Additional packages may be used.
- ES7 is desirable
- Prettier (https://prettier.io) is desirable (easily installed as a Visual Studio Code extension)
- lodash (https://lodash.com) is recommended
- You don't have to use a database. Everything can be computed in arrays or objects.

### Structure of data

#### Task

```json
{
  "id": "123-123-123-123",
  "name": "test",
  "isPriority": false,
  "isCompleted": true,
  "created_at": "2019-11-02T18:28:06.447Z",
  "completed_at": "2019-11-02T18:29:06.447Z"
}
```

## Server

- Communication via websocket/Socket.IO
- New tasks are queued as uncompleted
- Tasks have to be completed individually and in order
- Tasks with priority are processed preferentially
- Task without priority need 5-10 seconds (random) to complete processing
- The server notifies all clients about:
  - New task
  - Task processing completed
- All clients should be synchronised with all tasks at any time
- Newly connecting clients should receive all previous tasks

### Code

- The Socket.IO server is implemented in `server/index.js` and can be started by running `npm run server`. It will run on `http://localhost:4000`
- ISO timestamps can be generated with `moment().toISOString()` (`import moment from "moment"`)
- Unique IDs can be generated with `uuid()` (`import uuid from "uuid/v4"`)

### Packages

- https://github.com/socketio/socket.io
- additional packages may be used

## React-Frontend

- The form should consist of a an input element for the name, a checkbox to set the tasks priority and a submit button
- Tasks should be displayed in a table or a list
- New tasks should be recevied asynchronously via Socket.IO and automatically be added to the table/list (sort sort descending by timestamp)
- Uncompleted tasks should be marked accordingly (for example with the existing spinner component in `components/Spinner`)
- Prioritized Tasks should be marked accordingly
- The Socket.IO client should be implemented with the Context feature. The Context should contain the complete state and pass tasks and the functionalty to create new tasks to the main component as props.
- Create a single component for every element (form, list of tasks, single tasks) to keep the code simple and demonstrate the data flow.

### Code

- Frontend is already implemented with webpack, babel and react and can be started by running `npm start`. It will run on `http://localhost:3000`
- Entry component is `src/containers/Root/index.jsx`
- Usage of bootstrap and `react-bootstrap` is preferred

### packages

- https://github.com/react-bootstrap/react-bootstrap
- https://github.com/socketio/socket.io-client
- https://github.com/moment/moment
- additional packages may be used
