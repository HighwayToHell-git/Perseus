<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>⚔️ Perseus — README</title>
<style>
:root{--bg:#0d1117;--panel:#161b22;--border:#30363d;--text:#e6edf3;--muted:#8b949e;--blue:#58a6ff;--orange:#f0883e;--purple:#bc8cff}
*{box-sizing:border-box}body{margin:0;background:radial-gradient(circle at top,#182235 0,#0d1117 45%);color:var(--text);font:16px/1.7 -apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif}.wrap{width:min(1050px,calc(100% - 28px));margin:auto;padding:45px 0 70px}header{text-align:center;padding:30px 15px 42px;border-bottom:1px solid var(--border);margin-bottom:28px}h1{font-size:clamp(2.7rem,8vw,5rem);margin:0;letter-spacing:-3px}h2{border-bottom:1px solid var(--border);padding-bottom:9px;margin-top:0}h3{color:var(--blue)}p,li{color:#c9d1d9}.tag{color:var(--muted);font-size:1.1rem;max-width:760px;margin:8px auto 24px}.badges{display:flex;justify-content:center;flex-wrap:wrap;gap:7px}.badge{border:1px solid var(--border);border-radius:7px;overflow:hidden;background:var(--panel);font-size:.82rem}.badge span{padding:3px 8px;display:inline-block}.label{color:var(--muted);background:#21262d}.value{font-weight:600}section{background:#161b22bb;border:1px solid var(--border);border-radius:12px;padding:26px;margin:18px 0;box-shadow:0 8px 28px #0002}.notice,.quote{padding:13px 17px;border-radius:7px;margin:18px 0}.notice{border-left:4px solid var(--orange);background:#f0883e12}.quote{border-left:4px solid var(--purple);background:#bc8cff0d;font-style:italic}code,pre{font-family:ui-monospace,SFMono-Regular,Consolas,monospace}code{background:#21262d;border:1px solid var(--border);padding:2px 6px;border-radius:5px}pre{background:#010409;border:1px solid var(--border);border-radius:8px;padding:18px;overflow:auto}.arch{text-align:center;color:var(--blue);font:bold 18px/2 monospace}.roadmap{display:grid;grid-template-columns:repeat(auto-fit,minmax(225px,1fr));gap:9px;padding:0;list-style:none}.roadmap li{background:#0f141b;border:1px solid var(--border);border-radius:7px;padding:8px 11px;margin:0}.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:12px}.card{background:#0f141b;border:1px solid var(--border);border-radius:8px;padding:15px}a{color:var(--blue);text-decoration:none}a:hover{text-decoration:underline}footer{text-align:center;color:var(--muted);padding-top:30px}footer strong{display:block;color:var(--text);font-size:1.25rem}@media(max-width:600px){.wrap{padding-top:18px}section{padding:19px}}
</style>
</head>
<body><main class="wrap">
<header><h1>⚔️ Perseus</h1><p class="tag">An experimental operating system built from scratch, starting with a 16-bit x86 bootloader and kernel written in NASM.</p><div class="badges"><div class="badge"><span class="label">status</span><span class="value">idea</span></div><div class="badge"><span class="label">version</span><span class="value">-1.0</span></div><div class="badge"><span class="label">architecture</span><span class="value">x86</span></div><div class="badge"><span class="label">assembly</span><span class="value">NASM</span></div><div class="badge"><span class="label">license</span><span class="value">Apache-2.0</span></div></div></header>

<section><h2>📖 About</h2><p>Perseus is an experimental operating system created as a hobby project, a way to improve low-level programming skills, and a long-term portfolio project.</p><p>The project starts with a 16-bit x86 bootloader and kernel written in NASM.</p><p>The long-term goal is to evolve Perseus from a tiny experimental kernel into a fully usable user-oriented operating system, eventually supporting 32-bit and 64-bit x86.</p><div class="notice">⚠️ <b>Project status:</b> Perseus is currently at the idea/concept stage. No functional kernel or bootloader has been implemented yet.</div></section>

<section><h2>🎯 Goals</h2><ul><li>Learn how computers boot and operate at a low level</li><li>Build a bootloader from scratch</li><li>Build a kernel from scratch</li><li>Work directly with memory and hardware</li><li>Develop a custom driver system</li><li>Implement disk and filesystem support</li><li>Build a simple shell</li><li>Run user programs</li><li>Eventually create a complete user-oriented operating system</li></ul><p>Perseus is primarily a hobby, learning, and portfolio project.</p></section>

<section><h2>🚧 Current Status</h2><p><b>Version:</b> -1<br><b>Status:</b> Idea / Concept</p><p>Currently, Perseus exists mainly as a concept and development plan.</p><h3>MVP</h3><ul><li>Boot on real hardware</li><li>Run in 32-bit mode</li><li>Provide a basic shell</li><li>Access a filesystem</li><li>Support FAT32 or EXT4</li><li>Provide an interface for custom drivers</li><li>Run basic user programs</li></ul><div class="quote">«Perseus should eventually run on real hardware, not only inside a virtual machine.»</div><p>Virtualization and emulation tools such as QEMU will be used during development and testing.</p></section>

<section><h2>🧠 Architecture</h2><p>Development starts with 16-bit x86.</p><div class="arch">16-bit x86<br>↓<br>32-bit x86<br>↓<br>64-bit x86</div><p>NASM Assembly will be the primary language during the early stages.</p><p>At a later stage, especially around the 32-bit LTS release, C may be introduced for parts of the kernel.</p></section>

<section><h2>🛠️ Technology</h2><ul><li><b>NASM</b> — bootloader and kernel</li><li><b>C</b> — possible future kernel components</li><li><b>x86</b> — target architecture</li><li><b>QEMU</b> — development and testing</li></ul><p>No external libraries are currently planned.</p></section>

<section><h2>💿 Boot &amp; Installation</h2><ol><li>Download the latest Perseus ISO</li><li>Write it to a USB drive</li><li>Boot a computer from the USB drive</li><li>Start Perseus</li></ol><p>The future installation process may look something like:</p><pre>Perseus OS

perseus&gt; Perseus-install

Installing Perseus...
[████████████████████] 100%

Installation complete.

perseus&gt; _</pre><div class="notice"><b>Perseus-install</b> is currently only a concept and is not implemented.</div></section>

<section><h2>🖥️ User Interface</h2><p>The early versions of Perseus will use a text-based shell.</p><pre>Perseus OS
Copyright ...

perseus&gt; _</pre><p>The long-term goal is to move beyond a simple shell and provide a complete environment for users.</p></section>
<section><h2>🗂️ Filesystem</h2><ul><li>FAT32</li><li>EXT4</li></ul><p>The exact implementation order has not yet been decided.</p></section>
<section><h2>🔌 Drivers</h2><p>A major goal of Perseus is to provide an environment where developers can create their own drivers.</p><p>The long-term idea is to make hardware support modular rather than tightly coupled to the entire kernel.</p></section>

<section><h2>🗺️ Roadmap</h2><ul class="roadmap"><li>☐ 16-bit bootloader</li><li>☐ Kernel loading</li><li>☐ 16-bit kernel</li><li>☐ Basic memory management</li><li>☐ Basic I/O</li><li>☐ Enter protected mode</li><li>☐ 32-bit kernel</li><li>☐ Shell</li><li>☐ Disk access</li><li>☐ Filesystem support</li><li>☐ FAT32 / EXT4</li><li>☐ Driver system</li><li>☐ User programs</li><li>☐ C integration</li><li>☐ 32-bit LTS</li><li>☐ 64-bit support</li><li>☐ Full user-oriented OS</li></ul><p>The roadmap will change as development progresses.</p></section>
<section><h2>📦 Releases</h2><p>Official builds are planned to be distributed as <code>.iso</code> images through the project's GitHub repository.</p><p>Development builds may be unstable and should only be used for testing.</p></section>
<section><h2>🤝 Contributing</h2><p>Perseus is intended to be an open-source project. Contribution guidelines will be added once the project reaches a stage where external contributions become practical.</p><ul><li>Contribution guidelines</li><li>Source tree structure</li><li>Coding style</li><li>Pull request requirements</li><li>Driver development documentation</li><li>Kernel development documentation</li></ul></section>
<section><h2>📜 License</h2><p>Perseus is licensed under the Apache License 2.0.</p><p>You are free to:</p><ul><li>Use the project privately</li><li>Use it commercially</li><li>Modify the source code</li><li>Redistribute the original or modified version</li><li>Create derivative works</li><li>Use the code in proprietary projects</li></ul><p>When redistributing the project, you must include a copy of the Apache License 2.0, preserve applicable copyright notices, clearly indicate modified files, and follow the terms of the license.</p><p>The software is provided without warranty. The complete license text is available in <code>LICENSE</code>.</p></section>
<section><h2>👤 Author</h2><div class="cards"><div class="card"><b>HighwayToHell-git</b><br>Daniil</div><div class="card">💬 Telegram: <a href="https://t.me/daniil_21_36" target="_blank" rel="noopener">@daniil_21_36</a></div></div></section>
<section><h2>✍️ README</h2><p>This README was initially written by ChatGPT based on the project's description and development plans provided by the author.</p></section>
<section><h2>⚠️ Disclaimer</h2><p>Perseus is an experimental operating system project.</p><p>Early versions are not intended for production use or for storing important data.</p><p>When experimenting with bootloaders, kernels, disks, and filesystems, use a virtual machine or dedicated test hardware.</p></section>
<footer><strong>⚔️ Perseus</strong>From bootloader to user OS.<br>Built from scratch. One instruction at a time.</footer>
</main></body></html>
