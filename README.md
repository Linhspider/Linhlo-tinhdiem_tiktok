<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>TikTok Live Gift Points</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f9;
      margin: 0;
      padding: 20px;
      text-align: center;
    }
    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
    }
    th, td {
      padding: 10px;
      border: 1px solid #ddd;
    }
    th {
      background-color: #333;
      color: white;
    }
    td {
      background-color: #fff;
    }
    .button {
      margin-top: 20px;
      padding: 10px 20px;
      font-size: 16px;
      background-color: #008CBA;
      color: white;
      border: none;
      cursor: pointer;
      border-radius: 5px;
    }
  </style>
</head>
<body>
  <h1>TikTok Live Gift Point Tracker</h1>
  <div>
    <button class="button" onclick="fetchGiftData()">Lấy dữ liệu quà tặng từ TikTok Live</button>
  </div>
  <h2>Tổng điểm: <span id="totalPoints">0</span></h2>
  <script>
    async function fetchGiftData() {
      const accessToken = 'YOUR_ACCESS_TOKEN'; // Thay YOUR_ACCESS_TOKEN bằng Access Token của bạn
      const apiUrl = 'https://open.tiktokapis.com/v2/live/gifts'; // API endpoint

      try {
        const response = await fetch(apiUrl, {
          method: 'GET',
          headers: {
            'Authorization': `Bearer ${accessToken}`
          }
        });

        if (!response.ok) {
          throw new Error('Lỗi khi lấy dữ liệu từ API');
        }

        const data = await response.json();
        let totalPoints = 0;

        // Giả sử mỗi quà tặng là 1 điểm, tính toán tổng điểm
        data.gifts.forEach(gift => {
          totalPoints += gift.count * 1; // Điều chỉnh theo giá trị điểm của từng loại quà nếu cần
        });

        document.getElementById('totalPoints').textContent = totalPoints;
      } catch (error) {
        console.error('Có lỗi xảy ra:', error);
      }
    }
  </script>
</body>
</html>
