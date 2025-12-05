# Triam-Udom-Report-System
<html lang="th">
  <body style="background-color: #f8bbd0;">
<head>
  <meta charset="UTF-8" />
  <title>ระบบรับแจ้งปัญหาและข้อขัดข้องในการปฏิบัติงาน โรงเรียนเตรียมอุดมศึกษา</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <style>
    /* ------- โครงร่างและฟอนต์พื้นฐาน ------- */
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI",
        sans-serif;
      background: #ECD4D4;
      color: #222;
    }

    .page {
      max-width: 1100px;
      margin: 0 auto;
      padding: 16px;
    }

    header {
      padding: 16px 0;
      text-align: center;
    }

    header h1 {
      margin: 0;
      font-size: 1.6rem;
      font-weight: 700;
      color: #1f3b7b;
    }

    header p {
      margin-top: 8px;
      font-size: 0.95rem;
      color: #555;
    }

    /* ------- Card / กล่องข้อมูล ------- */
    .card {
      background: #fff;
      border-radius: 12px;
      padding: 16px 18px;
      margin-bottom: 16px;
      box-shadow: 0 4px 10px rgba(31, 59, 123, 0.08);
    }

    .card-title {
      font-size: 1.05rem;
      font-weight: 600;
      margin-bottom: 12px;
      color: #1f3b7b;
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .card-title span.icon {
      font-size: 1.2rem;
    }

    /* ------- ฟอร์มและเลย์เอาต์ ------- */
    form {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 12px 16px;
    }

    @media (max-width: 768px) {
      form {
        grid-template-columns: 1fr;
      }
    }

    .form-group {
      display: flex;
      flex-direction: column;
      gap: 4px;
    }

    label {
      font-size: 0.9rem;
      font-weight: 600;
      color: #333;
    }

    label .required {
      color: #d62828;
      margin-left: 4px;
    }

    input[type="text"],
    input[type="tel"],
    input[type="email"],
    select,
    textarea {
      font: inherit;
      padding: 8px 10px;
      border-radius: 8px;
      border: 1px solid #ccd4ea;
      outline: none;
      transition: border 0.15s, box-shadow 0.15s, background 0.15s;
      background: #fdfdff;
    }

    input[type="text"]:focus,
    input[type="tel"]:focus,
    input[type="email"]:focus,
    select:focus,
    textarea:focus {
      border-color: #1f3b7b;
      box-shadow: 0 0 0 2px rgba(31, 59, 123, 0.15);
      background: #ffffff;
    }

    textarea {
      min-height: 80px;
      resize: vertical;
    }

    .full-row {
      grid-column: 1 / -1;
    }

    .hint {
      font-size: 0.8rem;
      color: #777;
    }

    /* ------- ปุ่ม ------- */
    .form-actions {
      grid-column: 1 / -1;
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      justify-content: flex-end;
      margin-top: 4px;
    }

    .btn {
      border: none;
      border-radius: 999px;
      padding: 8px 16px;
      font-size: 0.9rem;
      cursor: pointer;
      font-weight: 600;
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .btn-primary {
      background: #1f3b7b;
      color: #fff;
    }

    .btn-primary:hover {
      background: #173060;
    }

    .btn-secondary {
      background: #e0e5f4;
      color: #1f3b7b;
    }

    .btn-secondary:hover {
      background: #d1d7ef;
    }

    .btn-muted {
      background: #f1f1f5;
      color: #555;
      cursor: default;
    }

    /* ------- ข้อความแจ้งเตือน ------- */
    .alert {
      padding: 8px 12px;
      border-radius: 10px;
      font-size: 0.9rem;
      margin-bottom: 10px;
      display: none;
    }

    .alert-success {
      background: #d8f5d8;
      border: 1px solid #71c671;
      color: #225522;
    }

    .alert-error {
      background: #ffe3e3;
      border: 1px solid #ff9b9b;
      color: #7d2222;
    }

    /* ------- ตารางแสดงรายการปัญหา ------- */
    .table-actions {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      gap: 8px;
      margin-bottom: 10px;
    }

    .table-actions label {
      font-size: 0.85rem;
      font-weight: 500;
    }

    .table-actions select {
      max-width: 260px;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.85rem;
      background: #fff;
      border-radius: 10px;
      overflow: hidden;
    }

    thead {
      background: #1f3b7b;
      color: #fff;
    }

    th,
    td {
      padding: 8px 10px;
      border-bottom: 1px solid #e1e4f0;
      text-align: left;
      vertical-align: top;
    }

    th {
      font-weight: 600;
    }

    tbody tr:nth-child(even) {
      background: #f7f8ff;
    }

    .status-badge {
      display: inline-block;
      padding: 2px 8px;
      border-radius: 999px;
      font-size: 0.78rem;
      background: #fff2cc;
      color: #9a6a00;
      border: 1px solid #f2cf66;
    }

    .no-data {
      text-align: center;
      padding: 16px;
      color: #777;
      font-size: 0.9rem;
    }
  </style>
</head>
<body>
  <div class="page">
    <header>
      <h1>ระบบรายงานปัญหา โรงเรียนเตรียมอุดมศึกษา</h1>
      <p>
        สำหรับครู บุคลากร นักเรียน และผู้ปกครอง ในการรายงานปัญหาต่าง ๆ
        เพื่อส่งต่อไปยังกลุ่มบริหารที่เกี่ยวข้องอย่างเป็นระบบ
      </p>
    </header>

    <!-- กล่องแจ้งเตือน -->
    <div id="alertBox" class="alert"></div>

    <!-- ฟอร์มรายงานปัญหา -->
    <div class="card">
      <div class="card-title">
        <span class="icon">📝</span>
        ฟอร์มรายงานปัญหา
      </div>

      <form id="issueForm">
        <!-- ประเภทผู้ใช้งาน -->
        <div class="form-group">
          <label for="userRole">
            ประเภทผู้ใช้งาน
            <span class="required">*</span>
          </label>
          <select id="userRole" required>
            <option value="">-- กรุณาเลือก --</option>
            <option value="ครู">ครู</option>
            <option value="บุคลากร">บุคลากร</option>
            <option value="นักเรียน">นักเรียน</option>
            <option value="ผู้ปกครอง">ผู้ปกครอง</option>
          </select>
        </div>

        <!-- ชื่อ-สกุล -->
        <div class="form-group">
          <label for="userName">
            ชื่อ–สกุล
            <span class="required">*</span>
          </label>
          <input
            type="text"
            id="userName"
            placeholder="ตัวอย่าง: นางสาวศรีสุดา ใจดี"
            required
          />
        </div>

        <!-- สังกัด/ห้องเรียน -->
        <div class="form-group">
          <label for="userDept">สังกัด/ห้องเรียน</label>
          <input
            type="text"
            id="userDept"
            placeholder="ตัวอย่าง: ตึกคุณหญิงหรั่งฯ, กลุ่มสาระภาษาไทย"
          />
        </div>

        <!-- ช่องทางติดต่อ -->
        <div class="form-group">
          <label for="userContact">ช่องทางติดต่อ (โทรศัพท์/อีเมล)</label>
          <input
            type="text"
            id="userContact"
            placeholder="ตัวอย่าง: 08x-xxx-xxxx หรือ email@example.com"
          />
        </div>

        <!-- กลุ่มบริหารที่รับเรื่อง -->
        <div class="form-group">
          <label for="adminGroup">
            กลุ่มบริหารที่เกี่ยวข้อง
            <span class="required">*</span>
          </label>
          <select id="adminGroup" required>
            <option value="">-- กรุณาเลือก --</option>
            <option value="สำนักผู้อำนวยการ">สำนักผู้อำนวยการ</option>
            <option value="กลุ่มบริหารวิชาการ">กลุ่มบริหารวิชาการ</option>
            <option value="กลุ่มบริหารกิจการนักเรียนและบุคลากร">
              กลุ่มบริหารกิจการนักเรียนและบุคลากร
            </option>
            <option value="กลุ่มบริหารงบประมาณ">กลุ่มบริหารงบประมาณ</option>
            <option value="กลุ่มบริหารทั่วไป">กลุ่มบริหารทั่วไป</option>
          </select>
        </div>

        <!-- ประเภทปัญหา -->
        <div class="form-group">
          <label for="issueType">ประเภทปัญหา</label>
          <select id="issueType">
            <option value="">-- เลือกประเภทปัญหา --</option>
            <option value="การเรียนการสอน">การเรียนการสอน</option>
            <option value="อาคารสถานที่/ความปลอดภัย">
              อาคารสถานที่/ความปลอดภัย
            </option>
            <option value="วินัยนักเรียน">วินัยนักเรียน</option>
            <option value="ระบบสารสนเทศ/เทคโนโลยี">
              ระบบสารสนเทศ/เทคโนโลยี
            </option>
            <option value="งบประมาณ/วัสดุอุปกรณ์">
              งบประมาณ/วัสดุอุปกรณ์
            </option>
            <option value="อื่น ๆ">อื่น ๆ</option>
          </select>
        </div>

        <!-- หัวข้อปัญหา -->
        <div class="form-group full-row">
          <label for="issueTitle">
            หัวข้อปัญหา
            <span class="required">*</span>
          </label>
          <input
            type="text"
            id="issueTitle"
            placeholder="สรุปปัญหาโดยย่อ เช่น ห้องเรียนร้อนมาก เครื่องปรับอากาศไม่ทำงาน"
            required
          />
        </div>

        <!-- รายละเอียดปัญหา -->
        <div class="form-group full-row">
          <label for="issueDetail">
            รายละเอียดปัญหา
            <span class="required">*</span>
          </label>
          <textarea
            id="issueDetail"
            placeholder="โปรดอธิบายรายละเอียด ปัญหาเกิดเมื่อใด เกิดที่ไหน และส่งผลอย่างไรบ้าง"
            required
          ></textarea>
        </div>

        <!-- ระดับความเร่งด่วน -->
        <div class="form-group">
          <label for="urgency">
            ระดับความเร่งด่วน
          </label>
          <select id="urgency">
            <option value="ปกติ">ปกติ</option>
            <option value="เร่งด่วน">เร่งด่วน</option>
            <option value="ด่วนมาก">ด่วนมาก</option>
          </select>
        </div>

        <!-- ปุ่มแนบไฟล์ (ตัวอย่างตำแหน่ง) -->
        <div class="form-group">
          <label>แนบไฟล์/รูปภาพ (ตัวอย่างตำแหน่ง)</label>
          <button type="button" class="btn btn-muted">
            📎 แนบไฟล์ (ตัวอย่าง)
          </button>
          <span class="hint">
            หมายเหตุ: ในตัวอย่างนี้ยังไม่รองรับการอัปโหลดไฟล์จริง เป็นเพียงตำแหน่งปุ่มตัวอย่าง
          </span>
        </div>

        <!-- ปุ่มส่ง / ล้างข้อมูล -->
        <div class="form-actions">
          <button type="reset" class="btn btn-secondary">
            ล้างข้อมูล
          </button>
          <button type="submit" class="btn btn-primary">
            ส่งรายงานปัญหา
          </button>
        </div>
      </form>
    </div>

    <!-- ตารางแสดงปัญหาที่รายงานแล้ว -->
    <div class="card">
      <div class="card-title">
        <span class="icon">📋</span>
        รายการปัญหาที่รายงานในระบบนี้
      </div>

      <div class="table-actions">
        <div>
          <label for="filterAdminGroup">
            กรองตามกลุ่มบริหาร:
          </label>
        </div>
        <div>
          <select id="filterAdminGroup">
            <option value="all">แสดงทุกกลุ่มบริหาร</option>
            <option value="สำนักผู้อำนวยการ">เฉพาะ สำนักผู้อำนวยการ</option>
            <option value="กลุ่มบริหารวิชาการ">เฉพาะ กลุ่มบริหารวิชาการ</option>
            <option value="กลุ่มบริหารกิจการนักเรียนและบุคลากร">
              เฉพาะ กลุ่มบริหารกิจการนักเรียนและบุคลากร
            </option>
            <option value="กลุ่มบริหารงบประมาณ">
              เฉพาะ กลุ่มบริหารงบประมาณ
            </option>
            <option value="กลุ่มบริหารทั่วไป">เฉพาะ กลุ่มบริหารทั่วไป</option>
          </select>
        </div>
      </div>

      <div style="overflow-x: auto;">
        <table>
          <thead>
            <tr>
              <th style="min-width: 120px;">วันที่–เวลา</th>
              <th style="min-width: 90px;">ประเภทผู้ใช้</th>
              <th style="min-width: 120px;">กลุ่มบริหารที่รับเรื่อง</th>
              <th style="min-width: 160px;">หัวข้อปัญหา</th>
              <th style="min-width: 100px;">ความเร่งด่วน</th>
              <th style="min-width: 120px;">สถานะ</th>
            </tr>
          </thead>
          <tbody id="issueTableBody">
            <tr>
              <td colspan="6" class="no-data">
                ยังไม่มีข้อมูลการรายงานปัญหา ระบบจะแสดงข้อมูลที่นี่เมื่อมีการส่งฟอร์ม
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>

  <script>
    // เก็บข้อมูลปัญหาทั้งหมด (ในหน้านี้เท่านั้น ไม่เชื่อมต่อฐานข้อมูลจริง)
    const issues = [];

    const issueForm = document.getElementById("issueForm");
    const alertBox = document.getElementById("alertBox");
    const issueTableBody = document.getElementById("issueTableBody");
    const filterAdminGroup = document.getElementById("filterAdminGroup");

    // แสดงข้อความแจ้งเตือน
    function showAlert(message, type = "success") {
      alertBox.textContent = message;
      alertBox.className = "alert"; // รีเซ็ต
      if (type === "success") {
        alertBox.classList.add("alert-success");
      } else if (type === "error") {
        alertBox.classList.add("alert-error");
      }
      alertBox.style.display = "block";

      // ซ่อนข้อความอัตโนมัติหลัง 5 วินาที
      setTimeout(() => {
        alertBox.style.display = "none";
      }, 5000);
    }

    // ฟังก์ชันเรนเดอร์ตาราง
    function renderTable() {
      const selectedGroup = filterAdminGroup.value;
      const filtered =
        selectedGroup === "all"
          ? issues
          : issues.filter((item) => item.adminGroup === selectedGroup);

      if (filtered.length === 0) {
        issueTableBody.innerHTML =
          '<tr><td colspan="6" class="no-data">ยังไม่มีข้อมูลการรายงานปัญหาตรงตามเงื่อนไขที่เลือก</td></tr>';
        return;
      }

      issueTableBody.innerHTML = "";
      filtered.forEach((issue) => {
        const tr = document.createElement("tr");

        tr.innerHTML = `
          <td>${issue.timestamp}</td>
          <td>${issue.userRole}</td>
          <td>${issue.adminGroup}</td>
          <td>${issue.issueTitle}</td>
          <td>${issue.urgency}</td>
          <td><span class="status-badge">รอพิจารณา</span></td>
        `;

        issueTableBody.appendChild(tr);
      });
    }

    // เมื่อมีการเปลี่ยนการกรองตาราง
    filterAdminGroup.addEventListener("change", renderTable);

    // เมื่อส่งฟอร์ม
    issueForm.addEventListener("submit", function (event) {
      event.preventDefault();

      const userRole = document.getElementById("userRole").value.trim();
      const userName = document.getElementById("userName").value.trim();
      const adminGroup = document.getElementById("adminGroup").value.trim();
      const issueTitle = document.getElementById("issueTitle").value.trim();
      const issueDetail = document.getElementById("issueDetail").value.trim();
      const userDept = document.getElementById("userDept").value.trim();
      const userContact = document.getElementById("userContact").value.trim();
      const issueType = document.getElementById("issueType").value.trim();
      const urgency = document.getElementById("urgency").value.trim() || "ปกติ";

      // ตรวจสอบฟิลด์ที่จำเป็น
      if (!userRole || !userName || !adminGroup || !issueTitle || !issueDetail) {
        showAlert(
          "กรุณากรอกข้อมูลที่มีเครื่องหมาย * ให้ครบถ้วนก่อนส่งรายงาน",
          "error"
        );
        return;
      }

      // เวลาปัจจุบัน (รูปแบบไทย)
      const now = new Date();
      let timestamp;
      try {
        timestamp = now.toLocaleString("th-TH", {
          dateStyle: "short",
          timeStyle: "short",
        });
      } catch (e) {
        // fallback ถ้าเบราว์เซอร์ไม่รองรับ option dateStyle/timeStyle
        timestamp = now.toLocaleString("th-TH");
      }

      // สร้างอ็อบเจ็กต์ปัญหา
      const issueData = {
        userRole,
        userName,
        userDept,
        userContact,
        adminGroup,
        issueType,
        issueTitle,
        issueDetail,
        urgency,
        timestamp,
        status: "รอพิจารณา",
      };

      // เก็บลง array
      issues.push(issueData);

      // เคลียร์ฟอร์ม
      issueForm.reset();

      // เรียกเรนเดอร์ตารางใหม่
      renderTable();

      // แสดงข้อความสำเร็จ
      showAlert("ระบบได้รับรายงานปัญหาแล้ว ขอบคุณค่ะ/ครับ", "success");
    });
  </script>
</body>
</html>
