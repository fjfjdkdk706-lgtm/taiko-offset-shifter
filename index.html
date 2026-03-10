<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>段位TJA #DELAY 一括調整ツール</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/encoding-japanese/2.0.0/encoding.min.js"></script>
    <style>
        :root {
            --bg-color: #f0f2f5;
            --card-bg: #ffffff;
            --primary: #27ae60;
            --text-main: #333333;
            --border-color: #e1e4e8;
        }
        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 40px 20px;
            margin: 0;
        }
        .container {
            width: 100%;
            max-width: 600px;
            background: var(--card-bg);
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
        }
        h1 {
            text-align: center;
            font-size: 1.5rem;
            color: #2c3e50;
            margin-bottom: 20px;
        }
        .box {
            border: 2px dashed #bdc3c7;
            border-radius: 8px;
            padding: 30px 20px;
            text-align: center;
            cursor: pointer;
            background: #fafafa;
            transition: 0.3s;
            margin-bottom: 20px;
        }
        .box:hover {
            border-color: var(--primary);
            background: #e9f7ef;
        }
        .box p { margin: 0; font-weight: bold; color: #7f8c8d; }
        
        .form-group {
            margin-bottom: 20px;
            background: #f8f9fa;
            padding: 20px;
            border-radius: 8px;
            border: 1px solid var(--border-color);
        }
        .form-group label {
            display: block;
            font-weight: bold;
            margin-bottom: 8px;
        }
        input[type="number"] {
            width: 100%;
            padding: 10px;
            border-radius: 6px;
            border: 1px solid #bdc3c7;
            font-size: 1.1rem;
            box-sizing: border-box;
            margin-bottom: 10px;
        }
        .radio-group {
            display: flex;
            gap: 20px;
            margin-top: 10px;
            margin-bottom: 15px;
        }
        .radio-group label {
            font-weight: normal;
            display: flex;
            align-items: center;
            cursor: pointer;
            margin: 0;
        }
        .radio-group input {
            transform: scale(1.2);
            margin-right: 8px;
            cursor: pointer;
        }

        .guide-box {
            background: #e8f4fd;
            border-left: 4px solid #3498db;
            padding: 12px 15px;
            border-radius: 4px;
            font-size: 0.9rem;
            line-height: 1.6;
            color: #2c3e50;
            margin-top: 15px;
        }
        .guide-box ul {
            margin: 5px 0 0 0;
            padding-left: 20px;
        }
        
        button {
            width: 100%;
            padding: 15px;
            background-color: var(--primary);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            opacity: 0.5;
            pointer-events: none;
            transition: 0.2s;
        }
        button.active { opacity: 1; pointer-events: auto; }
        button:hover { filter: brightness(0.9); }

        #log {
            margin-top: 20px;
            background: #2d3436;
            color: #dfe6e9;
            padding: 15px;
            border-radius: 6px;
            height: 150px;
            overflow-y: auto;
            font-family: Consolas, monospace;
            font-size: 0.85rem;
            white-space: pre-wrap;
        }
        .log-ok { color: #55efc4; }
        .log-info { color: #74b9ff; }
        .log-err { color: #ff7675; }
    </style>
</head>
<body>

<div class="container">
    <h1>段位TJA #DELAY 一括調整ツール</h1>

    <div class="box" id="dropZone" onclick="document.getElementById('fileInput').click()">
        <p>ここに 段位TJAファイル をドラッグ＆ドロップ</p>
        <p style="font-size:0.85rem; font-weight:normal; margin-top:5px;">(またはクリックして選択)</p>
        <input type="file" id="fileInput" accept=".tja" style="display:none">
    </div>

    <div class="form-group">
        <label>ずらす値を入力 (ファイル内の全 #DELAY に適用)</label>
        <div class="radio-group">
            <label><input type="radio" name="unit" value="s" checked> 秒 (そのまま) で指定</label>
            <label><input type="radio" name="unit" value="ms"> ミリ秒 (ms) で指定</label>
        </div>
        <input type="number" id="shiftAmount" step="0.001" placeholder="例: 0.05 / -0.02">
        
        <div class="guide-box">
            <strong>💡 目安と変換式</strong><br>
            10ms ＝ 0.01秒<br>
            100ms ＝ 0.1秒<br>
            1000ms ＝ 1秒<br>
            <hr style="border:0; border-top:1px dashed #b9cce0; margin: 8px 0;">
            <strong>⚙️ ＋ / － の使い分け</strong>
            <ul>
                <li>プレイしていて<strong>遅延が気になる人</strong>は <strong>プラス (+)</strong> に</li>
                <li>「この曲、<strong>遅くないか？</strong>」と思ったら <strong>マイナス (-)</strong> に</li>
            </ul>
        </div>
    </div>

    <button id="runBtn">一括調整して上書き保存</button>

    <div id="log">TJAファイルを読み込んでください...</div>
</div>

<script>
    const fileInput = document.getElementById('fileInput');
    const dropZone = document.getElementById('dropZone');
    const runBtn = document.getElementById('runBtn');
    const logArea = document.getElementById('log');
    const shiftInput = document.getElementById('shiftAmount');
    const radioUnits = document.querySelectorAll('input[name="unit"]');

    let targetFile = null;
    let fileContent = "";

    // 単位切り替え時の表示変更
    radioUnits.forEach(radio => {
        radio.addEventListener('change', (e) => {
            if (e.target.value === 'ms') {
                shiftInput.placeholder = "例: 50 / -20";
                shiftInput.step = "1";
            } else {
                shiftInput.placeholder = "例: 0.05 / -0.02";
                shiftInput.step = "0.001";
            }
        });
    });

    function log(msg, type = '') {
        const div = document.createElement('div');
        div.textContent = `> ${msg}`;
        if(type) div.className = `log-${type}`;
        logArea.appendChild(div);
        logArea.scrollTop = logArea.scrollHeight;
    }

    // ファイル処理
    fileInput.addEventListener('change', e => handleFile(e.target.files[0]));
    dropZone.addEventListener('dragover', e => { e.preventDefault(); dropZone.style.borderColor = '#27ae60'; });
    dropZone.addEventListener('dragleave', e => { e.preventDefault(); dropZone.style.borderColor = '#bdc3c7'; });
    dropZone.addEventListener('drop', e => {
        e.preventDefault();
        dropZone.style.borderColor = '#bdc3c7';
        if(e.dataTransfer.files.length > 0) handleFile(e.dataTransfer.files[0]);
    });

    function handleFile(file) {
        if (!file || !file.name.toLowerCase().endsWith('.tja')) {
            log('エラー: TJAファイルを選択してください。', 'err');
            return;
        }
        targetFile = file;
        logArea.innerHTML = '';
        log(`読込完了: ${file.name}`, 'info');

        const reader = new FileReader();
        reader.onload = (e) => {
            // encoding.js を使って文字コードを判定・変換して読み込み
            const uint8Array = new Uint8Array(e.target.result);
            const detected = Encoding.detect(uint8Array);
            const unicodeArray = Encoding.convert(uint8Array, {
                to: 'UNICODE',
                from: detected || 'SJIS'
            });
            fileContent = Encoding.codeToString(unicodeArray);
            
            runBtn.classList.add('active');
            runBtn.textContent = "一括調整して保存";
        };
        reader.readAsArrayBuffer(file);
    }

    // 変換・保存処理
    runBtn.addEventListener('click', () => {
        if (!targetFile || !fileContent) return;

        let inputVal = parseFloat(shiftInput.value);
        if (isNaN(inputVal)) {
            log('エラー: ずらす値を正しく入力してください。', 'err');
            return;
        }

        const unit = document.querySelector('input[name="unit"]:checked').value;
        let shiftVal = unit === 'ms' ? inputVal / 1000 : inputVal;
        
        let lines = fileContent.split(/\r?\n/);
        let modifiedCount = 0;
        
        log(`=== 処理開始 (入力: ${inputVal}${unit} -> 実質シフト量: ${shiftVal > 0 ? '+' : ''}${shiftVal}秒) ===`, 'info');

        for (let i = 0; i < lines.length; i++) {
            let line = lines[i];

            const delayMatch = line.match(/^(\s*#DELAY\s+)(-?\d+(\.\d+)?)(.*)$/i);
            if (delayMatch) {
                let oldVal = parseFloat(delayMatch[2]);
                let newVal = oldVal + shiftVal;
                newVal = Number(newVal.toFixed(4));
                lines[i] = delayMatch[1] + newVal + delayMatch[4];
                log(`L${i+1} [#DELAY] ${oldVal} -> ${newVal}`, 'ok');
                modifiedCount++;
            }
        }

        if (modifiedCount === 0) {
            log('変更する対象 (#DELAY) が見つかりませんでした。', 'err');
            return;
        }

        log(`合計 ${modifiedCount} 箇所を書き換えました！保存します。`, 'ok');

        // 改行コードをCRLFに統一して文字列化
        const finalText = lines.join('\r\n');
        
        // encoding.js を使って Unicode から Shift-JIS に変換 (BOMなし)
        const unicodeArrayForExport = Encoding.stringToCode(finalText);
        const sjisArray = Encoding.convert(unicodeArrayForExport, {
            to: 'SJIS',
            from: 'UNICODE'
        });
        
        // Uint8ArrayとしてBlobを作成 (これで純粋なShift-JISファイルになる)
        const blob = new Blob([new Uint8Array(sjisArray)], { type: 'application/octet-stream' });
        
        const link = document.createElement('a');
        link.href = URL.createObjectURL(blob);
        link.download = targetFile.name; 
        document.body.appendChild(link);
        link.click();
        document.body.removeChild(link);
    });
</script>
</body>
</html>
