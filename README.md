<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RCS - Result & Certificate System</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body { 
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }
        
        .box { 
            background: white; 
            padding: 30px; 
            border-radius: 15px; 
            max-width: 650px; 
            margin: 30px auto; 
            box-shadow: 0 10px 40px rgba(0,0,0,0.2);
            animation: fadeIn 0.5s ease-in;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        h2, h3, h4 {
            color: #333;
            margin-bottom: 15px;
        }
        
        h2 {
            text-align: center;
            font-size: 28px;
            color: #667eea;
        }
        
        input, button, textarea { 
            width: 100%; 
            padding: 12px; 
            margin: 10px 0; 
            border-radius: 8px; 
            border: 2px solid #e0e0e0; 
            box-sizing: border-box;
            font-size: 15px;
            transition: all 0.3s;
        }
        
        input:focus, textarea:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }
        
        button { 
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white; 
            cursor: pointer; 
            border: none; 
            font-weight: bold; 
            transition: all 0.3s;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        button:hover { 
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }
        
        button:active {
            transform: translateY(0);
        }
        
        .hidden { 
            display: none; 
        }
        
        table { 
            width: 100%; 
            border-collapse: collapse; 
            margin-top: 15px; 
            background: #fff;
            border-radius: 8px;
            overflow: hidden;
        }
        
        th, td { 
            border: 1px solid #e0e0e0; 
            padding: 12px; 
            text-align: left; 
        }
        
        th { 
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            font-weight: 600;
            text-transform: uppercase;
            font-size: 13px;
            letter-spacing: 0.5px;
        }
        
        tr:hover {
            background: #f8f9ff;
        }
        
        .student-img { 
            width: 100px; 
            height: 100px; 
            border-radius: 50%; 
            object-fit: cover; 
            border: 4px solid #667eea;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
            margin: 10px auto;
            display: block;
        }
        
        .notice { 
            background: linear-gradient(to right, #fff3cd, #ffe69c);
            padding: 15px; 
            border-left: 5px solid #ffc107; 
            margin-bottom: 20px; 
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }
        
        .notice b {
            color: #856404;
            font-size: 16px;
        }
        
        .res-input { 
            width: 90px !important; 
            padding: 6px !important; 
            margin: 0 !important;
            text-align: center;
            font-weight: bold;
        }
        
        .btn-logout {
            background: linear-gradient(135deg, #f44336 0%, #d32f2f 100%);
            width: auto; 
            padding: 8px 20px;
            font-size: 14px;
        }
        
        .btn-logout:hover {
            box-shadow: 0 5px 15px rgba(244, 67, 54, 0.4);
        }
        
        .btn-notice {
            background: linear-gradient(135deg, #17a2b8 0%, #138496 100%);
        }
        
        .btn-save {
            background: linear-gradient(135deg, #28a745 0%, #218838 100%);
        }
        
        .btn-delete {
            padding: 6px 12px; 
            background: linear-gradient(135deg, #f44336 0%, #d32f2f 100%);
            font-size: 13px;
            width: auto;
        }
        
        .admin-header {
            display: flex; 
            justify-content: space-between; 
            align-items: center;
            margin-bottom: 25px;
            padding-bottom: 15px;
            border-bottom: 2px solid #f0f0f0;
        }
        
        .profile-card {
            background: linear-gradient(135deg, #f8f9ff 0%, #e8ecff 100%);
            padding: 25px;
            border-radius: 12px;
            text-align: center;
            margin-top: 15px;
        }
        
        .profile-card h3 {
            color: #667eea;
            margin: 15px 0 10px 0;
            font-size: 24px;
        }
        
        .profile-card p {
            color: #666;
            font-size: 15px;
            margin: 8px 0;
        }
        
        .result-box {
            background: linear-gradient(135deg, #e9ecef 0%, #dee2e6 100%);
            padding: 15px;
            border-radius: 10px;
            margin-top: 15px;
            box-shadow: inset 0 2px 5px rgba(0,0,0,0.1);
        }
        
        .result-box strong {
            color: #333;
            font-size: 18px;
        }
        
        hr {
            border: none;
            border-top: 2px solid #f0f0f0;
            margin: 25px 0;
        }
        
        .table-wrapper {
            overflow-x: auto;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }
        
        textarea {
            font-family: inherit;
            resize: vertical;
            min-height: 80px;
        }
        
        input[type="file"] {
            padding: 10px;
            background: #f8f9fa;
            cursor: pointer;
        }
        
        input[type="file"]:hover {
            background: #e9ecef;
        }
        
        @media (max-width: 600px) {
            .box {
                padding: 20px;
                margin: 15px;
            }
            
            .admin-header {
                flex-direction: column;
                align-items: flex-start;
            }
            
            .btn-logout {
                width: 100%;
                margin-top: 10px;
            }
            
            table {
                font-size: 13px;
            }
            
            th, td {
                padding: 8px 5px;
            }
        }
    </style>
</head>
<body>

<div id="login-div" class="box">
    <h2>🏫 School Login System</h2>
    <input type="text" id="user" placeholder="Student ID বা Admin Name লিখুন">
    <input type="password" id="pass" placeholder="Password (শুধু Admin এর জন্য)">
    <button onclick="login()">🔐 Login করুন</button>
</div>

<div id="admin-div" class="box hidden">
    <div class="admin-header">
        <h3>👨‍💼 Admin: Pritam</h3>
        <button onclick="logout()" class="btn-logout">Logout</button>
    </div>
    
    <h4>📢 Notice Update করুন</h4>
    <textarea id="notic-in" placeholder="নোটিস এখানে লিখুন..."></textarea>
    <button onclick="saveNotice()" class="btn-notice">Update Notice</button>
    
    <hr>
    
    <h4>➕ নতুন Student যোগ করুন</h4>
    <input type="text" id="sid" placeholder="Student ID (Unique)">
    <input type="text" id="sname" placeholder="Student এর নাম">
    <input type="text" id="sinfo" placeholder="Class/Section">
    <input type="file" id="sphoto" accept="image/*">
    <button onclick="addStudent()" class="btn-save">Save Student</button>
    
    <hr>
    
    <h4>📋 Student List & Results</h4>
    <div class="table-wrapper">
        <table id="list">
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Name</th>
                    <th>Result</th>
                    <th>Action</th>
                </tr>
            </thead>
            <tbody id="tbody"></tbody>
        </table>
    </div>
</div>

<div id="student-div" class="box hidden">
    <div id="notice-out" class="notice"></div>
    <div id="profile"></div>
    <button onclick="logout()" class="btn-logout">Logout</button>
</div>

<script>
    // Database - localStorage থেকে data নিচ্ছে
    let db = JSON.parse(localStorage.getItem('school_data')) || [];

    // Page load হলে session check করবে
    window.onload = function() {
        let session = localStorage.getItem('login_session');
        if (session === "admin") {
            show('admin-div');
            render();
            loadNotice();
        } else if (session) {
            loginAsStudent(session);
        }
    };

    // Login Function
    function login() {
        let u = document.getElementById('user').value.trim();
        let p = document.getElementById('pass').value;

        // Admin Login Check - আপনার credentials
        if (u === "Chhanda" && p === "raypritam") {
            localStorage.setItem('login_session', 'admin');
            show('admin-div');
            render();
            loadNotice();
        } else {
            // Student Login Check (শুধু ID দিয়ে)
            let s = db.find(x => x.id === u);
            if (s) {
                localStorage.setItem('login_session', u);
                loginAsStudent(u);
            } else { 
                alert("❌ ভুল ID অথবা Admin Password!"); 
            }
        }
    }

    // Student হিসেবে Login
    function loginAsStudent(studentId) {
        let s = db.find(x => x.id === studentId);
        if (s) {
            show('student-div');
            let n = localStorage.getItem('school_note') || "এখনো কোনো নোটিস নেই";
            document.getElementById('notice-out').innerHTML = "<b>📢 Notice:</b> " + n;
            document.getElementById('profile').innerHTML = `
                <div class="profile-card">
                    <img src="${s.img}" class="student-img">
                    <h3>${s.name}</h3>
                    <p><strong>ID:</strong> ${s.id}</p>
                    <p><strong>Info:</strong> ${s.info}</p>
                    <div class="result-box">
                        <strong>📊 Result: ${s.result || 'এখনো প্রকাশিত হয়নি'}</strong>
                    </div>
                </div>
            `;
        }
    }

    // Notice Load করা (admin panel এ)
    function loadNotice() {
        let savedNotice = localStorage.getItem('school_note') || '';
        document.getElementById('notic-in').value = savedNotice;
    }

    // নতুন Student Add করা
    function addStudent() {
        let id = document.getElementById('sid').value.trim();
        let name = document.getElementById('sname').value.trim();
        let info = document.getElementById('sinfo').value.trim();
        let file = document.getElementById('sphoto').files[0];

        if (!id || !name || !file) { 
            alert("⚠️ সব তথ্য পূরণ করুন!"); 
            return; 
        }
        
        if (db.find(x => x.id === id)) { 
            alert("❌ এই আইডি ইতিমধ্যে রয়েছে!"); 
            return; 
        }

        let reader = new FileReader();
        reader.onload = function(e) {
            let img = new Image();
            img.src = e.target.result;
            img.onload = function() {
                // Image Compress করা (APK এর মতো)
                let canvas = document.createElement('canvas');
                let ctx = canvas.getContext('2d');
                canvas.width = 150; 
                canvas.height = 150; 
                ctx.drawImage(img, 0, 0, 150, 150);
                let compressedImg = canvas.toDataURL('image/jpeg', 0.7);

                db.push({id, name, info, img: compressedImg, result: ""});
                localStorage.setItem('school_data', JSON.stringify(db));
                alert("✅ স্টুডেন্ট সফলভাবে যোগ হয়েছে!");
                render();
                
                // Form Clear করা
                document.getElementById('sid').value = "";
                document.getElementById('sname').value = "";
                document.getElementById('sinfo').value = "";
                document.getElementById('sphoto').value = "";
            };
        };
        reader.readAsDataURL(file);
    }

    // Result Update করা (inline edit)
    function updateResult(index, val) {
        db[index].result = val;
        localStorage.setItem('school_data', JSON.stringify(db));
    }

    // Notice Save করা
    function saveNotice() {
        localStorage.setItem('school_note', document.getElementById('notic-in').value);
        alert("✅ নোটিস আপডেট হয়েছে!");
    }

    // Student List Render করা
    function render() {
        let h = "";
        if (db.length === 0) {
            h = '<tr><td colspan="4" style="text-align: center; padding: 20px; color: #999;">এখনো কোনো student নেই</td></tr>';
        } else {
            db.forEach((s, i) => {
                h += `<tr>
                    <td><strong>${s.id}</strong></td>
                    <td>${s.name}</td>
                    <td><input type="text" class="res-input" value="${s.result || ''}" placeholder="GPA" onchange="updateResult(${i}, this.value)"></td>
                    <td><button onclick="del(${i})" class="btn-delete">Delete</button></td>
                </tr>`;
            });
        }
        document.getElementById('tbody').innerHTML = h;
    }

    // Student Delete করা
    function del(i) {
        if(confirm("⚠️ আপনি কি নিশ্চিত এই student কে মুছে দিতে চান?")) {
            db.splice(i, 1);
            localStorage.setItem('school_data', JSON.stringify(db));
            render();
            alert("✅ Student মুছে দেওয়া হয়েছে!");
        }
    }

    // Logout করা
    function logout() {
        localStorage.removeItem('login_session');
        location.reload();
    }

    // Page Show/Hide করা
    function show(id) {
        document.getElementById('login-div').classList.add('hidden');
        document.getElementById('admin-div').classList.add('hidden');
        document.getElementById('student-div').classList.add('hidden');
        document.getElementById(id).classList.remove('hidden');
    }
    
    // Enter key press এ login
    document.addEventListener('keypress', function(e) {
        if (e.key === 'Enter' && !document.getElementById('login-div').classList.contains('hidden')) {
            login();
        }
    });
</script>

</body>
</html>
