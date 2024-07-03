# control-buttons
a direction buttons for robot that will help us control the directions easily after link it with the robot 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Control Buttons</title>
    <style>
        .controls {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 10px;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }
        .horizontal {
            display: flex;
            gap: 10px;
        }
    </style>
</head>
<body>
    <div class="controls">
        <button onclick="move('up')">Forward</button>
        <div class="horizontal">
            <button onclick="move('left')">Left</button>
            <button onclick="stop()">Stop</button>
            <button onclick="move('right')">Right</button>
        </div>
        <button onclick="move('down')">Backward</button>
    </div>

    <script>
        function move(direction) {
            console.log(`Move: ${direction}`);
            // Implement movement logic here
        }

        function stop() {
            console.log('Stop');
            // Implement stop logic here
        }
    </script>
</body>
</html>
![image](https://github.com/Ohidy/control-buttons/assets/173767059/3ab81759-c35d-4466-a012-392e2eec28ef)
