# CSS

## 表格

```css
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .tb1 {
            width: 400px;
            border: 3px solid blue;
            border-collapse: collapse;
        }

        td,
        th {
            border: 1px solid gray;
        }

        thead {
            background-color: hotpink;
            color: #ffffff;
            text-transform: capitalize;
        }

        tbody {
            background-color: darkcyan;
            text-align: center;
        }
        tbody tr:nth-child(2n){
            background-color: darkorchid;
        }
        tbody tr:nth-child(2n+1){
            background-color:darkolivegreen;
        }
        tbody tr:hover{
            background-color: firebrick;
        }
        tbody td:hover{
            background-color: lightblue;
        }
    </style>
</head>

<body>
    <table class="tb1">
        <thead>
            <tr>
                <th>column1</th>
                <th>column2</th>
                <th>column3</th>
                <th>column4</th>
            </tr>
            <tr>
                <th colspan="2">column1</th>
                <th colspan="2">column2</th>

            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1</td>
                <td>2</td>
                <td>3</td>
                <td>4</td>
            </tr>
            <tr>
                <td>1</td>
                <td>2</td>
                <td rowspan="3">3</td>
                <td>4</td>
            </tr>
            <tr>
                <td>1</td>
                <td>2</td>

                <td>4</td>
            </tr>
            <tr>
                <td>1</td>
                <td>2</td>

                <td>4</td>
            </tr>
        </tbody>
    </table>
</body>

</html>
```



