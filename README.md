# Kesar-ff-unban-id

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Free Fire | Unban Appeal</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, sans-serif;
    }

    body {
      min-height: 100vh;
      background: radial-gradient(circle at top, #401010, #090909 65%);
      color: white;
      padding: 25px 15px;
    }

    header {
      text-align: center;
      padding: 25px 10px;
    }

    header h1 {
      color: #ff3939;
      font-size: clamp(28px, 6vw, 42px);
      text-transform: uppercase;
      letter-spacing: 2px;
    }

    header p {
      color: #ccc;
      margin-top: 10px;
    }

    .container {
      max-width: 550px;
      margin: 10px auto;
      padding: 28px;
      background: #151515;
      border: 1px solid #492323;
      border-radius: 15px;
      box-shadow: 0 0 30px #ff202018;
    }

    .notice {
      background: #281b12;
      border-left: 4px solid #ff9c36;
      color: #ffd8a8;
      padding: 12px;
      border-radius: 5px;
      font-size: 13px;
      line-height: 1.6;
      margin-bottom: 22px;
    }

    label {
      display: block;
      margin: 17px 0 8px;
      font-size: 14px;
      color: #eee;
    }

    input, select, textarea {
      width: 100%;
      padding: 13px;
      border: 1px solid #383838;
      border-radius: 7px;
      background: #0c0c0c;
      color: white;
      font-size: 15px;
      outline: none;
    }

    input:focus, select:focus, textarea:focus {
      border-color: #ff3939;
    }

    textarea {
      min-height: 125px;
      resize: vertical;
      line-height: 1.5;
    }

    .check {
      display: flex;
      gap: 10px;
      align-items: flex-start;
      font-size: 13px;
      line-height: 1.5;
      color: #ccc;
      margin: 20px 0;
    }

    .check input {
      width: auto;
      margin-top: 3px;
    }

    button {
      width: 100%;
      padding: 15px;
      border: none;
      border-radius: 7px;
      background: #e52b2b;
      color: white;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
      transition: 0.2s;
    }

    button:hover {
      background: #ff4545;
      transform: translateY(-1px);
    }

    #result {
      display: none;
      margin-top: 18px;
      padding: 15px;
      background: #18271a;
      border-radius: 7px;
      color: #b9ffc4;
      line-height: 1.6;
      overflow-wrap: anywhere;
    }

    footer {
      text-align: center;
      color: #888;
      font-size: 12px;
      margin: 25px auto 10px;
      line-height: 1.8;
    }

    footer a {
      color: #ff7777;
    }
  </style>
</head>
<body>

  <header>
    <h1>FREE FIRE</h1>
    <p>Account Unban Appeal Portal</p>
  </header>

  <main class="container">
    <div class="notice">
      <strong>Important:</strong> This is an unofficial fan-made
      appeal form, not a Garena website. Submitting here does not
      contact Garena or guarantee an unban.
    </div>

    <form id="appealForm">
      <label for="uid">Player UID *</label>
      <input
        id="uid"
        name="uid"
        type="text"
        inputmode="numeric"
        pattern="[0-9]{5,20}"
        minlength="5"
        maxlength="20"
        placeholder="Enter your Player UID"
        required
      >

      <label for="nickname">In-game Nickname *</label>
      <input
        id="nickname"
        name="nickname"
        type="text"
        maxlength="40"
        placeholder="Enter your nickname"
        required
      >

      <label for="reason">Ban Issue *</label>
      <select id="reason" name="reason" required>
        <option value="">Select an issue</option>
        <option>Permanent ban</option>
        <option>Temporary ban</option>
        <option>Account suspended</option>
        <option>Other account issue</option>
      </select>

      <label for="details">Appeal Message *</label>
      <textarea
        id="details"
        name="details"
        minlength="20"
        maxlength="1500"
        placeholder="Explain your issue and why you are requesting a review..."
        required
      ></textarea>

      <label class="check">
        <input type="checkbox" id="confirm" required>
        <span>I confirm that the information I entered is accurate.
        I understand that this form does not submit an appeal to Garena.</span>
      </label>

      <button type="submit">PREPARE MY APPEAL</button>
    </form>

    <div id="result" role="status" aria-live="polite"></div>
  </main>

  <footer>
    Unofficial fan-made project. Not affiliated with Garena.
    <br>
    For actual account support, visit
    <a href="https://ffsupport.garena.com/" target="_blank"
       rel="noopener noreferrer">Garena Free Fire Support</a>.
  </footer>

  <script>
    const form = document.getElementById("appealForm");
    const result = document.getElementById("result");

    form.addEventListener("submit", function(event) {
      event.preventDefault();

      if (!form.reportValidity()) return;

      const uid = document.getElementById("uid").value.trim();
      const nickname =
        document.getElementById("nickname").value.trim();
      const reason = document.getElementById("reason").value;
      const details =
        document.getElementById("details").value.trim();

      const subject = "Free Fire Account Appeal - UID " + uid;
      const message =
        "Player UID: " + uid + "\n" +
        "Nickname: " + nickname + "\n" +
        "Issue: " + reason + "\n\n" +
        "Appeal details:\n" + details;

      result.replaceChildren();

      const heading = document.createElement("strong");
      heading.textContent = "Your appeal draft is ready!";
      const paragraph = document.createElement("p");
      paragraph.textContent =
        "No information has been sent or saved by this website.";
      const copyButton = document.createElement("button");
      copyButton.type = "button";
      copyButton.style.marginTop = "12px";
      copyButton.textContent = "COPY APPEAL TEXT";

      copyButton.addEventListener("click", async function() {
        try {
          await navigator.clipboard.writeText(
            subject + "\n\n" + message
          );
          copyButton.textContent = "COPIED!";
        } catch {
          const area = document.createElement("textarea");
          area.value = subject + "\n\n" + message;
          result.appendChild(area);
          area.focus();
          area.select();
          copyButton.textContent =
            "Select and copy the text above";
        }
      });

      result.append(heading, paragraph, copyButton);
      result.style.display = "block";
      result.scrollIntoView({ behavior: "smooth", block: "nearest" });
    });
  </script>
</body>
</html>
