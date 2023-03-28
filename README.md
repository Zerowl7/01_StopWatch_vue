## Stopwatch App (Vue.js)

This is a simple stopwatch application. You can use it to track time spent on tasks or for other purposes.

![image](https://user-images.githubusercontent.com/67556607/228088533-73742353-13a2-4b2a-b037-153e12da40a7.png)

### Features

- Add multiple stopwatches
- Start, stop, and reset each stopwatch individually
- Responsively designed for different screen sizes

### How it works

The app is built with Vue.js, and uses a single component called StopwatchTimer to display each stopwatch. The main app component (App.vue) manages the list of timers and the grid layout.

When the user clicks the "Add" button, a new timer object is added to the timers array in the data section of App.vue. The StopwatchTimer component is then created for each timer in the array using v-for directive.

Each StopwatchTimer component has its own timer object passed as a prop, and it uses this to display and update the stopwatch.

### Installation and Setup

To install and run the application, follow these steps:

1. Clone the repository to your computer:
   git clone https://github.com/Zerowl7/Stopwatch-app-vue.git

2. Navigate to the project directory:
   cd Stopwatch-app-vue

3. Install dependencies:
   npm install

4. Run the application:
   npm run serve

5. Open a web browser and go to http://localhost:8080

### Usage

To start the timer, click the "Start" button. To pause the timer, click the "Pause" button. To reset the timer, click the "Reset" button.

### Contributing

If you would like to contribute to the project, you can create an issue or pull request on GitHub. When creating a pull request, be sure to describe all changes and add appropriate tests.

### Authors

Project author - [Zerowl7](https://github.com/Zerowl7)

### License

This project is licensed under the [MIT License](https://github.com/Zerowl7/Stopwatch-app-vue/blob/master/LICENSE).
