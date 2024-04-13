---
title: Gunicorn 是什麼？
---
- ## Gunicorn 是什麼？
- Gunicorn是一個WSGI HTTP服務器
- Gunicorn使用pre-fork worker模型，能夠在單個伺服器上處理大量的並發請求，提供高效能的Web服務。
- Gunicorn可以與Nginx、Apache等Web伺服器整合，透過反向代理的方式來處理靜態檔案和負載均衡，提高系統的效能和可靠性。
-
- ## Gunicorn 如何使用
- 安裝gunicorn
-
  ```shell
  pip install gunicorn
  ```
-
- 使用flask寫一個簡單的web服務
-
  ```python
  # main.py
  
  from flask import Flask
  
  app = Flask(__name__)
  
  
  @app.route('/')
  def index():
    return 'hello world'
  
  def main():
    app.run(debug=True)
  
  if __name__ == '__main__':
    main()
  ```
-
- 執行
-
  ```shell
  gunicorn main:app
  ```
- 打開瀏覽器，訪問`http://localhost:8000`，你應該會看到"Hello, World!"的輸出。
-
- ### 使用Gunicorn啟動應用程式時，你還可以使用更多的選項
  heading:: 3
-
  ```shell
  gunicorn -w 4 -b 127.0.0.1:8000 app:app
  ```
-
- 這將啟動4個工作進程（`-w 4`），並將應用程式綁定到`127.0.0.1:8000`（`-b 127.0.0.1:8000`）。
-
-
- ## 參考資料
- [flask中gunicorn的使用 - 理想幾歲 - 博客園 (cnblogs.com)](https://www.cnblogs.com/zongfa/p/12614459.html#:~:text=flask%E4%B8%ADgunicorn%E7%9A%84%E4%BD%BF%E7%94%A8%201%201%E3%80%81%E6%A8%A1%E5%9D%97%E5%AE%89%E8%A3%85%202%202%E3%80%81%E7%94%A8flask%E5%86%99%E4%B8%80%E4%B8%AA%E7%AE%80%E5%8D%95%E7%9A%84web%E6%9C%8D%E5%8A%A1,3%203%E3%80%81%E5%90%AF%E5%8A%A8%204%204%E3%80%81%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6%205%205%E3%80%81gunicorn%E5%90%AF%E5%8A%A8flask%E5%90%8E%EF%BC%8C%E8%AE%BF%E9%97%AEapi%E5%8D%B4%E6%8A%A5404)