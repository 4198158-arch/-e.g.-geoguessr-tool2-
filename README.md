# -e.g.-geoguessr-tool-
..
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GeoGuessr Coordinates Extractor</title>
    <style>
        :root {
            --bg-color: #0f172a;
            --card-bg: #1e293b;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --accent: #3b82f6;
            --accent-hover: #2563eb;
            --code-bg: #0b0f19;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            line-height: 1.6;
            margin: 0;
            padding: 40px 20px;
            display: flex;
            justify-content: center;
        }

        .container {
            max-width: 650px;
            width: 100%;
        }

        header {
            text-align: center;
            margin-bottom: 40px;
        }

        h1 {
            font-size: 2rem;
            margin-bottom: 10px;
            font-weight: 700;
        }

        .subtitle {
            color: var(--text-muted);
            margin-top: 0;
        }

        .card {
            background-color: var(--card-bg);
            border-radius: 12px;
            padding: 30px;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.3);
            margin-bottom: 24px;
        }

        h2 {
            font-size: 1.25rem;
            margin-top: 0;
            margin-bottom: 16px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        p {
            color: var(--text-muted);
            margin-bottom: 20px;
        }

        .btn-bookmark {
            display: inline-block;
            background-color: var(--accent);
            color: #fff;
            text-decoration: none;
            padding: 12px 24px;
            border-radius: 8px;
            font-weight: 600;
            cursor: move;
            transition: background-color 0.2s ease, transform 0.1s ease;
            user-select: none;
            text-align: center;
            box-shadow: 0 4px 6px -1px rgba(59, 130, 246, 0.3);
        }

        .btn-bookmark:hover {
            background-color: var(--accent-hover);
            transform: translateY(-1px);
        }

        .btn-bookmark:active {
            transform: translateY(1px);
        }

        .code-block {
            background-color: var(--code-bg);
            border: 1px solid #334155;
            border-radius: 6px;
            padding: 14px;
            font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
            font-size: 0.85rem;
            overflow-x: auto;
            white-space: pre-wrap;
            word-break: break-all;
            color: #38bdf8;
            max-height: 150px;
            margin-bottom: 12px;
        }

        .btn-copy {
            background-color: #334155;
            color: var(--text-main);
            border: none;
            padding: 8px 16px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.85rem;
            font-weight: 500;
            transition: background-color 0.2s;
        }

        .btn-copy:hover {
            background-color: #475569;
        }

        ol {
            margin: 0;
            padding-left: 20px;
            color: var(--text-muted);
        }

        li {
            margin-bottom: 10px;
        }

        code {
            background-color: rgba(255, 255, 255, 0.1);
            padding: 2px 6px;
            border-radius: 4px;
            font-family: monospace;
            color: #f43f5e;
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>GeoGuessr Coordinate Extractor</h1>
        <p class="subtitle">A client-side utility tool to retrieve active game coordinates</p>
    </header>

    <!-- Method 1: Easy Drag & Drop -->
    <div class="card">
        <h2>📦 Method 1: Drag & Drop (Easy)</h2>
        <p>Ensure your browser's Bookmarks/Favorites bar is visible (<code>Ctrl+Shift+B</code> or <code>Cmd+Shift+B</code>), then drag the button below directly into your bookmarks bar.</p>
        
        <div style="text-align: center; margin: 30px 0;">
            <a class="btn-bookmark" href="javascript:let x=async function(){function captureNetworkRequest(e){let capture_newtwork_request=[];let capture_resource=performance.getEntriesByType(`resource`);for(let i=0;i<capture_resource.length;i++){if(capture_resource[i].initiatorType==`xmlhttprequest`||capture_resource[i].initiatorType==`script`||capture_resource[i].initiatorType==`img`){if(!0){capture_newtwork_request.push(capture_resource[i].name)}}};return capture_newtwork_request};function jsonp(uri){return new Promise(function(resolve,reject){let id=`_`+Math.round(10000*Math.random());let callbackName=`jsonp_callback_`+id;window[callbackName]=function(data){delete window[callbackName];let ele=document.getElementById(id);ele.parentNode.removeChild(ele);resolve(data)};let src=uri+`&callback=`+callbackName;let script=document.createElement(`script`);script.src=src;script.id=id;script.addEventListener(`error`,reject);(document.getElementsByTagName(`head`)[0]||document.body||document.documentElement).appendChild(script)})};await jsonp(captureNetworkRequest().filter(url=>{return url.includes(`GeoPhoto`)})[0]).then(data=>{let coords=data[1][5][0][1][0].slice(2,4);window.open(`https://google.com{coords[0]},+${coords[1]}`)})};x()" title="Drag me to your bookmarks bar">
                📍 Extract Coordinates
            </a>
        </div>
    </div>

    <!-- Method 2: Manual Setup -->
    <div class="card">
        <h2>🛠️ Method 2: Manual Setup (Alternative)</h2>
        <p>If dragging does not work on your browser, follow these quick steps:</p>
        <ol>
            <li>Right-click your browser's bookmark bar and select <strong>Add Page</strong> or <strong>Bookmark this tab</strong>.</li>
            <li>Name it whatever you like (e.g., "Extract Location").</li>
            <li>Copy the exact raw code sequence block below and paste it directly into the <strong>URL</strong> or <strong>Address</strong> field.</li>
        </ol>
        
        <div style="margin-top: 20px;">
            <div class="code-block" id="bookmarkCode">javascript:let x=async function(){function captureNetworkRequest(e){let capture_newtwork_request=[];let capture_resource=performance.getEntriesByType(`resource`);for(let i=0;i<capture_resource.length;i++){if(capture_resource[i].initiatorType==`xmlhttprequest`||capture_resource[i].initiatorType==`script`||capture_resource[i].initiatorType==`img`){if(!0){capture_newtwork_request.push(capture_resource[i].name)}}};return capture_newtwork_request};function jsonp(uri){return new Promise(function(resolve,reject){let id=`_`+Math.round(10000*Math.random());let callbackName=`jsonp_callback_`+id;window[callbackName]=function(data){delete window[callbackName];let ele=document.getElementById(id);ele.parentNode.removeChild(ele);resolve(data)};let src=uri+`&callback=`+callbackName;let script=document.createElement(`script`);script.src=src;script.id=id;script.addEventListener(`error`,reject);(document.getElementsByTagName(`head`)[0]||document.body||document.documentElement).appendChild(script)})};await jsonp(captureNetworkRequest().filter(url=>{return url.includes(`GeoPhoto`)})[0]).then(data=>{let coords=data[1][5][0][1][0].slice(2,4);window.open(`https://google.com{coords[0]},+${coords[1]}`)})};x()</div>
            <button class="btn-copy" onclick="copyCode()">Copy Code</button>
        </div>
    </div>

    <!-- How to use -->
    <div class="card">
        <h2>🚀 Running the Tool</h2>
        <p>Navigate to any live game or exploration section inside GeoGuessr. Once your Street View scene has fully loaded up, simply click the new bookmarklet button you created in your bookmarks bar. The tool will parse the active session cache and attempt to launch a dedicated Google Maps interface pointing exactly to your current position.</p>
    </div>
</div>

<script>
    function copyCode() {
        const codeText = document.getElementById('bookmarkCode').innerText;
        navigator.clipboard.writeText(codeText).then(() => {
            const btn = document.querySelector('.btn-copy');
            btn.innerText = 'Copied!';
            btn.style.backgroundColor = '#10b981';
            setTimeout(() => {
                btn.innerText = 'Copy Code';
                btn.style.backgroundColor = '#334155';
            }, 2000);
        });
    }
</script>

</body>
</html>
