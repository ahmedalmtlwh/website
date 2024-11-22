<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>إدخال بيانات الدفع</title>
</head>
<body>
    <h2>إدخال بيانات الدفع</h2>
    <form id="paymentForm">
        <label for="userId">رقم المستخدم:</label>
        <input type="text" id="userId" required><br><br>

        <label for="amount">المبلغ المحول:</label>
        <input type="number" id="amount" step="0.01" required><br><br>

        <label for="phone">رقم الهاتف:</label>
        <input type="text" id="phone" required><br><br>

        <input type="submit" value="إتمام الدفع">
    </form>

    <script>
        document.getElementById("paymentForm").addEventListener("submit", function(event) {
            event.preventDefault();

            const userId = document.getElementById("userId").value;
            const amount = document.getElementById("amount").value;
            const phone = document.getElementById("phone").value;

            // التحقق من رقم الهاتف
            if (!validatePhoneNumber(phone)) {
                alert("رقم الهاتف غير صحيح! يجب أن يكون مكونًا من 9 أرقام.");
                return;
            }

            // إرسال البيانات إلى Postman أو API الخاص بك
            fetch("https://your-api-endpoint.com/validate-and-submit", {  // استبدل هذا بعنوان API أو Postman endpoint
                method: "POST",
                headers: {
                    "Content-Type": "application/json"
                },
                body: JSON.stringify({
                    user_id: userId,
                    amount: amount,
                    phone: phone
                })
            })
            .then(response => response.json())
            .then(data => {
                if (data.ok) {
                    alert("تم إضافة الرصيد بنجاح!");
                } else {
                    alert("حدث خطأ أثناء إضافة الرصيد.");
                }
            })
            .catch(error => {
                console.error("حدث خطأ: ", error);
                alert("حدث خطأ أثناء إرسال البيانات.");
            });
        });

        function validatePhoneNumber(phone) {
            const phoneRegex = /^[0-9]{9}$/;
            return phoneRegex.test(phone);
        }
    </script>
</body>
</html>
