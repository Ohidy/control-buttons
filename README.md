# control-buttons
a direction buttons for robot that will help us control the directions easily after link it with the robot 
i used visual studio code after searching a lot i found out it`s easy to use i made the interface using html code and linked it with phpmyadmin 
i couldn't figure out how to link them togather do it so i searched a lot but this video i will link it later actually helped a lot and i encurege beginners to watch it too to get the basic of php just so you can realize how it works
i rwote this code to make the buttons and the back ground (interface)
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Choose a Direction</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
    <style>
        body {
            background-color: rgb(0, 0, 0);
        }
        .btn-directions {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            font-size: 18px;
            font-weight: bold;
            color: white;
        }
        .btn-backwards {
            background-color: pink;
            margin-top: 20px;
        }
        .btn-stop {
            background-color: pink;
        }
        .btn-forwards {
            background-color: pink;
            margin-bottom: 20px;
        }
        .btn-left {
            background-color: pink;
            margin-right: 20px;
        }
        .btn-right {
            background-color: pink;
            margin-left: 20px;
        }
    </style>
</head>
<body>
    <div class="container text-center mt-5">
        <h1 style="color:white;">Choose a Direction</h1>
        <form action="handle_choice.php" method="post">
            <button type="submit" name="direction" value="backwards" class="btn btn-directions btn-backwards">Backwards</button><br>
            <button type="submit" name="direction" value="left" class="btn btn-directions btn-left">Left</button>
            <button type="submit" name="direction" value="stop" class="btn btn-directions btn-stop">Stop</button>
            <button type="submit" name="direction" value="right" class="btn btn-directions btn-right">Right</button><br>
            <button type="submit" name="direction" value="forwards" class="btn btn-directions btn-forwards">Forwards</button>
        </form>
    </div>
</body>
</html>

and then i opend it with (open with live server) to see my work on website and then i wrote my php code in another file named handel_choice.php


<?php
$host = 'localhost';
$username = 'root';
$password = '';
$dbname = 'directions_db';


$conn = new mysqli($host, $username, $password, $dbname);


if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}

if ($_SERVER['REQUEST_METHOD'] == 'POST' && isset($_POST['direction'])) {
    $direction = $_POST['direction'];

   
    $stmt = $conn->prepare("INSERT INTO user_choices (direction) VALUES (?)");
    $stmt->bind_param("s", $direction);
    $stmt->execute();
    $stmt->close();
}


$result = $conn->query("SELECT direction FROM user_choices ORDER BY chosen_at DESC LIMIT 1");
$last_choice = $result->fetch_assoc();

$conn->close();
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Last Chosen Direction</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
</head>
<body>
    <div class="container text-center mt-5">
        <h1>Last Chosen Direction</h1>
        <?php if ($last_choice): ?>
            <p>Your last chosen direction is: <strong><?php echo htmlspecialchars($last_choice['direction']); ?></strong></p>
        <?php else: ?>
            <p>No direction chosen yet.</p>
        <?php endif; ?>
        <a href="index.html" class="btn btn-primary">Choose Again</a>
    </div>
</body>
</html>
this code is meant to stores the chosen direction in the database we did in phpmyadmin and retrieves the last chosen direction but i will talk about that later 
here is the code after opening it on the server 
          ![Screenshot 2024-07-12 173018](https://github.com/user-attachments/assets/69b0537f-8d75-42c9-ab8f-910043370b2f)
          and when i use XAMPP it will look like this 
![Screenshot 2024-07-12 173315](https://github.com/user-attachments/assets/1f70cf64-b9c0-4afd-833f-fa169575f75e)
you will be conected to the database using xampp![Screenshot 2024-07-12 173500](https://github.com/user-attachments/assets/d2c2d233-7f1c-496a-b7b9-37294552f82a)

this is my data it has on table named user choices
![Screenshot 2024-07-12 173609](https://github.com/user-attachments/assets/bdfabbce-e92d-48fd-ae11-357ee3b7358d)
now i have my interface connected with the database and i can change it and edit easily
