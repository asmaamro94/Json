<?php
ini_set('display_errors', 1);
ini_set('display_startup_errors', 1);
error_reporting(E_ALL);

require_once 'config/config.php';

try {
    $results = $DB_con->query("SELECT * FROM foods");
} catch (Exception $e) {
    echo "error = " . $e;
}

$foods = $results->fetchAll(PDO::FETCH_ASSOC);
$new_array = array();
foreach ($foods as $food){
    array_push($new_array, $food);
}

header('Content-type: application/json');
echo json_encode($new_array);


