# front
Человек вводит сумму перевода, снизу автоматически должна высчитываться и отображаться комиссия, например 1%.
Далее представлен код страницы.


<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-+0n0xVW2eSR5OomGNYDnhzAbDsOXxcvSN1TPprVMTNDbiYZCxYbOOl7+AMvyTG2x" crossorigin="anonymous">
<head>

</head>
<div th:insert="~{mainClient :: copy}"></div>
</br>
<center>
    <div th:if="${param.success}">
        <div class="alert alert-info">
            Перевод отправлен на проверку!
        </div>
    </div>
    <form th:action="@{/transfer/otherBank}" method='POST' th:object="${transfer}">
        <div class="form-group">
            <label>Номер списания: </label>
            <select name="idCardFrom" >
                <option value="" > Выберите номер списания </option>
                <option th:each="card : ${cards}"
                        th:value="${card.id}"
                        th:utext="${card.number}"/>
            </select>
        </div>
        </br>
        <div class="form-group">
            <label>Номер карты получателя:</label>
            <input type="number" name ="number">
        </div>
        </br>
        <div class="form-group">
            <label >Сумма перевода  руб</label>
            <input type="number" name ="amount">

        </div>
        </br>
        <td><input name="submit" type="submit" value="Перевести" /></td>

    </form>
</center>
</body>
</html>
