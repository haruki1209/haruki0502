<!DOCTYPE html>
<html>
<head>
    <title>Schedule</title>
    <style>
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            border: 1px solid black;
            text-align: center;
            padding: 8px;
        }
        th {
            background-color: #f2f2f2;
        }
        .holiday {
            background-color: #ffcccc;
        }
        .available {
            color: green;
        }
        .unavailable {
            color: red;
        }
    </style>
</head>
<body>

<table id="scheduleTable">
    <tr>
        <th colspan="15">2024年8月</th>
    </tr>
    <tr>
        <th></th>
        <th>5 (Mon)</th>
        <th>6 (Tue)</th>
        <th>7 (Wed)</th>
        <th>8 (Thu)</th>
        <th>9 (Fri)</th>
        <th>10 (Sat)</th>
        <th>11 (Sun)</th>
        <th>12 (Mon)</th>
        <th>13 (Tue)</th>
        <th>14 (Wed)</th>
        <th>15 (Thu)</th>
        <th>16 (Fri)</th>
        <th>17 (Sat)</th>
        <th>18 (Sun)</th>
    </tr>
</table>

<script>
    const times = ["9:00", "9:30", "10:00", "10:30", "11:00", "11:30", "12:00", "12:30", "13:00", "13:30", "14:00", "14:30", "15:00", "15:30", "16:00", "16:30", "17:00", "17:30", "18:00", "18:30", "19:00", "19:30", "20:00"];
    const days = ["5 (Mon)", "6 (Tue)", "7 (Wed)", "8 (Thu)", "9 (Fri)", "10 (Sat)", "11 (Sun)", "12 (Mon)", "13 (Tue)", "14 (Wed)", "15 (Thu)", "16 (Fri)", "17 (Sat)", "18 (Sun)"];
    const table = document.getElementById("scheduleTable");

    // List of fixed holiday indices (for example: Sundays and specific dates)
    const fixedHolidays = [6, 13]; // 11 (Sun) and 18 (Sun) are fixed holidays

    // Populate the schedule table
    times.forEach(time => {
        let row = document.createElement("tr");
        let th = document.createElement("th");
        th.innerText = time;
        row.appendChild(th);

        for (let i = 0; i < days.length; i++) {
            let cell = document.createElement("td");

            // Check if it's a fixed holiday
            if (fixedHolidays.includes(i)) {
                cell.classList.add("holiday");
                cell.innerText = "休";
            } else {
                let randomValue = getRandomInt(2); // 0 or 1
                if (randomValue === 0) {
                    cell.classList.add("unavailable");
                    cell.innerText = "×";
                } else {
                    cell.classList.add("available");
                    cell.innerText = "○";
                }
            }
            row.appendChild(cell);
        }

        table.appendChild(row);
    });

    // Function to generate random number
    function getRandomInt(max) {
        return Math.floor(Math.random() * max);
    }
</script>

</body>
</html>