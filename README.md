 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>⚔️ Perseus — From bootloader to user OS</title>

    <!-- Fonts & Icons -->
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,400;14..32,500;14..32,600;14..32,700&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet" />
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />

    <style>
        /* ── Reset & Base ── */
        *,
        *::before,
        *::after {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --bg-primary: #0b0d11;
            --bg-secondary: #12161e;
            --bg-card: #171d28;
            --bg-card-hover: #1f2736;
            --bg-code: #0f131c;
            --border-color: #2a3346;
            --text-primary: #e8edf5;
            --text-secondary: #8e9bb5;
            --text-muted: #5d6b87;
            --accent-cyan: #5fc8e8;
            --accent-blue: #4d8bf7;
            --accent-purple: #a78bfa;
            --accent-green: #4ade80;
            --accent-orange: #fbbf24;
            --accent-red: #f87171;
            --shadow: 0 8px 32px rgba(0, 0, 0, 0.5);
            --radius: 12px;
            --radius-sm: 6px;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            background: var(--bg-primary);
            color: var(--text-primary);
            line-height: 1.7;
            padding: 2rem 1.5rem 4rem;
            min-height: 100vh;
        }

        /* ── Container ── */
        .container {
            max-width: 1000px;
            margin: 0 auto;
        }

        /* ── Badge Bar ── */
        .badge-bar {
            display: flex;
            flex-wrap: wrap;
            gap: 0.6rem 0.8rem;
            margin-bottom: 2rem;
            padding: 0.25rem 0;
        }

        .badge {
            display: inline-flex;
            align-items: center;
            gap: 0.4rem;
            font-size: 0.75rem;
            font-weight: 600;
            letter-spacing: 0.02em;
            padding: 0.25rem 0.9rem;
            border-radius: 100px;
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            color: var(--text-secondary);
            text-decoration: none;
            transition: border-color 0.2s, color 0.2s;
        }

        .badge i {
            font-size: 0.7rem;
        }

        .badge .status-dot {
            display: inline-block;
            width: 8px;
            height: 8px;
            border-radius: 50%;
            background: var(--accent-red);
            margin-right: 0.1rem;
        }

        .badge .status-dot.idea {
            background: var(--accent-red);
        }

        .badge .version {
            color: var(--accent-blue);
        }

        .badge .arch {
            color: var(--text-secondary);
        }

        .badge .nasm {
            color: var(--accent-orange);
        }

        .badge .license {
            color: var(--accent-green);
        }

        .badge:hover {
            border-color: var(--accent-cyan);
            color: var(--text-primary);
        }

        /* ── Header ── */
        .hero {
            margin-bottom: 3.5rem;
            padding: 2.5rem 0 1.5rem;
            border-bottom: 1px solid var(--border-color);
        }

        .hero h1 {
            font-size: 3rem;
            font-weight: 700;
            letter-spacing: -0.03em;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .hero h1 span {
            background: linear-gradient(135deg, var(--accent-cyan), var(--accent-purple));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero .tagline {
            font-size: 1.2rem;
            color: var(--text-secondary);
            margin-top: 0.4rem;
            font-weight: 400;
        }

        .hero .tagline i {
            color: var(--accent-orange);
            margin: 0 0.2rem;
        }

        /* ── Section Headers ── */
        section {
            margin-bottom: 3.5rem;
        }

        .section-title {
            font-size: 1.6rem;
            font-weight: 700;
            letter-spacing: -0.02em;
            margin-bottom: 1.2rem;
            display: flex;
            align-items: center;
            gap: 0.6rem;
            color: var(--text-primary);
        }

        .section-title i {
            color: var(--accent-cyan);
            font-size: 1.3rem;
            width: 1.6rem;
            text-align: center;
        }

        .section-title .icon-purple i {
            color: var(--accent-purple);
        }
        .section-title .icon-green i {
            color: var(--accent-green);
        }
        .section-title .icon-orange i {
            color: var(--accent-orange);
        }
        .section-title .icon-blue i {
            color: var(--accent-blue);
        }

        /* ── Cards ── */
        .card {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: var(--radius);
            padding: 1.6rem 2rem;
            margin-bottom: 1.2rem;
            transition: background 0.2s, border-color 0.2s;
        }

        .card:hover {
            background: var(--bg-card-hover);
            border-color: #334156;
        }

        .card p,
        .card li {
            color: var(--text-secondary);
        }

        .card strong {
            color: var(--text-primary);
            font-weight: 600;
        }

        .card ul,
        .card ol {
            padding-left: 1.5rem;
            margin: 0.6rem 0;
        }

        .card li {
            margin-bottom: 0.25rem;
        }

        .card .highlight {
            color: var(--accent-cyan);
            font-weight: 500;
        }

        .card .highlight-green {
            color: var(--accent-green);
            font-weight: 500;
        }

        .card .highlight-orange {
            color: var(--accent-orange);
            font-weight: 500;
        }

        /* ── Status / Alert boxes ── */
        .alert {
            background: rgba(248, 113, 113, 0.08);
            border-left: 4px solid var(--accent-red);
            padding: 1rem 1.4rem;
            border-radius: var(--radius-sm);
            margin: 0.8rem 0 1.2rem;
            color: var(--text-secondary);
        }

        .alert strong {
            color: var(--accent-red);
        }

        .alert-info {
            background: rgba(77, 139, 247, 0.08);
            border-left-color: var(--accent-blue);
        }

        .alert-info strong {
            color: var(--accent-blue);
        }

        .alert-success {
            background: rgba(74, 222, 128, 0.08);
            border-left-color: var(--accent-green);
        }

        .alert-success strong {
            color: var(--accent-green);
        }

        /* ── Code blocks ── */
        .code-block {
            background: var(--bg-code);
            border: 1px solid var(--border-color);
            border-radius: var(--radius-sm);
            padding: 1.2rem 1.5rem;
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.85rem;
            line-height: 1.8;
            overflow-x: auto;
            color: #c8d0e0;
            margin: 0.8rem 0;
            white-space: pre-wrap;
            word-break: break-word;
        }

        .code-block .prompt {
            color: var(--accent-green);
        }

        .code-block .cmd {
            color: var(--accent-cyan);
        }

        .code-block .comment {
            color: var(--text-muted);
            font-style: italic;
        }

        .code-block .output {
            color: var(--text-secondary);
        }

        .code-block .highlight-text {
            color: var(--accent-orange);
        }

        /* ── Roadmap ── */
        .roadmap-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 0.5rem 1.5rem;
            margin: 0.6rem 0 0.2rem;
        }

        .roadmap-item {
            display: flex;
            align-items: center;
            gap: 0.6rem;
            font-size: 0.95rem;
            color: var(--text-secondary);
            padding: 0.2rem 0;
        }

        .roadmap-item .checkbox {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 18px;
            height: 18px;
            border: 2px solid var(--border-color);
            border-radius: 4px;
            font-size: 0.6rem;
            color: var(--text-muted);
            flex-shrink: 0;
        }

        .roadmap-item .checkbox.done {
            border-color: var(--accent-green);
            background: rgba(74, 222, 128, 0.15);
            color: var(--accent-green);
        }

        .roadmap-item .checkbox.pending {
            border-color: var(--border-color);
        }

        .roadmap-item .label-done {
            color: var(--accent-green);
        }

        .roadmap-item .label-pending {
            color: var(--text-secondary);
        }

        /* ── Architecture flow ── */
        .arch-flow {
            display: flex;
            align-items: center;
            flex-wrap: wrap;
            gap: 0.3rem 0.8rem;
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.9rem;
            padding: 0.8rem 0 0.2rem;
            color: var(--text-secondary);
        }

        .arch-flow .arrow {
            color: var(--text-muted);
            font-size: 1.2rem;
        }

        .arch-flow .arch-box {
            background: var(--bg-code);
            border: 1px solid var(--border-color);
            border-radius: var(--radius-sm);
            padding: 0.2rem 1rem;
            font-weight: 500;
            color: var(--accent-cyan);
        }

        .arch-flow .arch-box.x86-16 {
            color: var(--accent-orange);
        }
        .arch-flow .arch-box.x86-32 {
            color: var(--accent-blue);
        }
        .arch-flow .arch-box.x86-64 {
            color: var(--accent-purple);
        }

        /* ── Footer / Divider ── */
        .footer-divider {
            margin: 3rem 0 2rem;
            border: 0;
            height: 1px;
            background: linear-gradient(to right, transparent, var(--border-color), transparent);
        }

        .footer-note {
            text-align: center;
            color: var(--text-muted);
            font-size: 0.9rem;
            letter-spacing: 0.02em;
        }

        .footer-note i {
            color: var(--accent-orange);
            margin: 0 0.2rem;
        }

        /* ── Links ── */
        a {
            color: var(--accent-cyan);
            text-decoration: none;
            transition: color 0.2s;
        }

        a:hover {
            color: var(--accent-blue);
            text-decoration: underline;
        }

        .link-plain {
            color: var(--text-secondary);
        }
        .link-plain:hover {
            color: var(--text-primary);
            text-decoration: none;
        }

        /* ── Responsive ── */
        @media (max-width: 700px) {
            body {
                padding: 1.2rem 1rem 3rem;
            }

            .hero h1 {
                font-size: 2.2rem;
                flex-wrap: wrap;
            }

            .hero .tagline {
                font-size: 1rem;
            }

            .section-title {
                font-size: 1.3rem;
            }

            .card {
                padding: 1.2rem 1.2rem;
            }

            .roadmap-grid {
                grid-template-columns: 1fr;
                gap: 0.3rem;
            }

            .badge-bar {
                gap: 0.4rem 0.6rem;
            }

            .badge {
                font-size: 0.65rem;
                padding: 0.2rem 0.7rem;
            }

            .arch-flow {
                font-size: 0.8rem;
                gap: 0.2rem 0.5rem;
            }

            .code-block {
                font-size: 0.75rem;
                padding: 1rem 1rem;
            }
        }

        @media (max-width: 450px) {
            .hero h1 {
                font-size: 1.8rem;
            }
            .card {
                padding: 1rem;
            }
            .badge {
                font-size: 0.6rem;
                padding: 0.15rem 0.6rem;
            }
        }

        /* ── Scrollbar ── */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: var(--bg-primary);
        }
        ::-webkit-scrollbar-thumb {
            background: var(--border-color);
            border-radius: 8px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: var(--text-muted);
        }

        /* small extra spacing */
        .mt-1 {
            margin-top: 0.6rem;
        }
        .mt-2 {
            margin-top: 1.2rem;
        }
        .mb-1 {
            margin-bottom: 0.6rem;
        }
        .flex {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            flex-wrap: wrap;
        }
    </style>
</head>

<body>
    <div class="container">

        <!-- ─── BADGE BAR ─── -->
        <div class="badge-bar">
            <span class="badge"><span class="status-dot idea"></span> status: idea</span>
            <span class="badge"><span class="version">version</span> -1.0</span>
            <span class="badge"><span class="arch">architecture</span> x86</span>
            <span class="badge"><span class="nasm">assembly</span> NASM</span>
            <span class="badge"><span class="license">license</span> Apache-2.0</span>
        </div>

        <!-- ─── HERO ─── -->
        <header class="hero">
            <h1>⚔️ <span>Perseus</span></h1>
            <p class="tagline">
                <i>«</i> An experimental operating system built from scratch,
                starting with a 16-bit x86 bootloader and kernel written in NASM. <i>»</i>
            </p>
        </header>

        <!-- ─── ABOUT ─── -->
        <section>
            <h2 class="section-title"><i class="fas fa-info-circle"></i> About</h2>
            <div class="card">
                <p>
                    <strong>Perseus</strong> is an experimental operating system created as a hobby project,
                    a way to improve low-level programming skills, and a long-term portfolio project.
                </p>
                <p class="mt-1">
                    The project starts with a 16-bit x86 bootloader and kernel written in NASM.
                    The long-term goal is to evolve Perseus from a tiny experimental kernel into
                    a fully usable user-oriented operating system, eventually supporting 32-bit and
                    64-bit x86.
                </p>
                <div class="alert">
                    <strong>⚠️ Project status:</strong> Perseus is currently at the idea/concept stage.
                    No functional kernel or bootloader has been implemented yet.
                </div>
            </div>
        </section>

        <!-- ─── GOALS ─── -->
        <section>
            <h2 class="section-title icon-purple"><i class="fas fa-bullseye"></i> Goals</h2>
            <div class="card">
                <p>The main goals of Perseus are:</p>
                <ul>
                    <li>Learn how computers boot and operate at a low level</li>
                    <li>Build a bootloader from scratch</li>
                    <li>Build a kernel from scratch</li>
                    <li>Work directly with memory and hardware</li>
                    <li>Develop a custom driver system</li>
                    <li>Implement disk and filesystem support</li>
                    <li>Build a simple shell</li>
                    <li>Run user programs</li>
                    <li>Eventually create a complete user-oriented operating system</li>
                </ul>
                <p class="mt-1"><em>Perseus is primarily a hobby, learning, and portfolio project.</em></p>
            </div>
        </section>

        <!-- ─── CURRENT STATUS ─── -->
        <section>
            <h2 class="section-title icon-orange"><i class="fas fa-code-branch"></i> Current Status</h2>
            <div class="card">
                <p><strong>Version:</strong> -1 &nbsp;·&nbsp; <strong>Status:</strong> Idea / Concept</p>
                <p class="mt-1">Currently, Perseus exists mainly as a concept and development plan.</p>

                <h4 style="margin: 1rem 0 0.4rem; color: var(--text-primary);">MVP</h4>
                <p>The first major milestone is a system that can:</p>
                <ul>
                    <li>Boot on real hardware</li>
                    <li>Run in 32-bit mode</li>
                    <li>Provide a basic shell</li>
                    <li>Access a filesystem</li>
                    <li>Support FAT32 or EXT4</li>
                    <li>Provide an interface for custom drivers</li>
                    <li>Run basic user programs</li>
                </ul>
                <div class="alert alert-info mt-1">
                    <strong>💡 The main idea is simple:</strong>
                    <em>«Perseus should eventually run on real hardware, not only inside a virtual machine.»</em>
                    <br />
                    Virtualization and emulation tools such as QEMU will be used during development and testing.
                </div>
            </div>
        </section>

        <!-- ─── ARCHITECTURE ─── -->
        <section>
            <h2 class="section-title icon-blue"><i class="fas fa-microchip"></i> Architecture</h2>
            <div class="card">
                <p>Development starts with <strong>16-bit x86</strong>. The planned evolution is:</p>

                <div class="arch-flow">
                    <span class="arch-box x86-16">16-bit x86</span>
                    <span class="arrow">▸</span>
                    <span class="arch-box x86-32">32-bit x86</span>
                    <span class="arrow">▸</span>
                    <span class="arch-box x86-64">64-bit x86</span>
                </div>

                <p class="mt-1">
                    <strong>NASM</strong> Assembly will be the primary language during the early stages.
                    At a later stage, especially around the 32-bit LTS release, C may be introduced for
                    parts of the kernel.
                </p>
            </div>
        </section>

        <!-- ─── TECHNOLOGY ─── -->
        <section>
            <h2 class="section-title icon-green"><i class="fas fa-wrench"></i> Technology</h2>
            <div class="card">
                <p>Current planned technology stack:</p>
                <ul>
                    <li><strong>NASM</strong> — bootloader and kernel</li>
                    <li><strong>C</strong> — possible future kernel components</li>
                    <li><strong>x86</strong> — target architecture</li>
                    <li><strong>QEMU</strong> — development and testing</li>
                </ul>
                <p class="mt-1">No external libraries are currently planned.</p>
            </div>
        </section>

        <!-- ─── BOOT & INSTALLATION ─── -->
        <section>
            <h2 class="section-title"><i class="fas fa-boot"></i> Boot &amp; Installation</h2>
            <div class="card">
                <p>Release builds are planned to be distributed as <strong>.iso</strong> images.</p>
                <p class="mt-1">The expected workflow:</p>
                <ol>
                    <li>Download the latest Perseus ISO</li>
                    <li>Write it to a USB drive</li>
                    <li>Boot a computer from the USB drive</li>
                    <li>Start Perseus</li>
                </ol>

                <p class="mt-1">The future installation process may look something like:</p>
                <div class="code-block">
                    <span class="comment">Perseus OS</span>
                    <br />
                    <span class="prompt">perseus&gt;</span> <span class="cmd">Perseus-install</span>
                    <br />
                    <span class="output">Installing Perseus...</span>
                    <br />
                    <span class="output">[████████████████████] 100%</span>
                    <br />
                    <span class="output">Installation complete.</span>
                    <br />
                    <span class="prompt">perseus&gt;</span> <span class="comment">_</span>
                </div>
                <div class="alert alert-info">
                    <strong>«Perseus-install»</strong> is currently only a concept and is not implemented.
                </div>
            </div>
        </section>

        <!-- ─── USER INTERFACE ─── -->
        <section>
            <h2 class="section-title icon-purple"><i class="fas fa-terminal"></i> User Interface</h2>
            <div class="card">
                <p>The early versions of Perseus will use a text-based shell.</p>
                <div class="code-block">
                    <span class="comment">Perseus OS</span>
                    <br />
                    <span class="comment">Copyright ...</span>
                    <br />
                    <br />
                    <span class="prompt">perseus&gt;</span> <span class="comment">_</span>
                </div>
                <p class="mt-1">The long-term goal is to move beyond a simple shell and provide a complete environment for users.</p>
            </div>
        </section>

        <!-- ─── FILESYSTEM ─── -->
        <section>
            <h2 class="section-title icon-orange"><i class="fas fa-folder-tree"></i> Filesystem</h2>
            <div class="card">
                <p>Planned filesystem support includes:</p>
                <ul>
                    <li><strong>FAT32</strong></li>
                    <li><strong>EXT4</strong></li>
                </ul>
                <p class="mt-1">The exact implementation order has not yet been decided.</p>
            </div>
        </section>

        <!-- ─── DRIVERS ─── -->
        <section>
            <h2 class="section-title icon-blue"><i class="fas fa-plug"></i> Drivers</h2>
            <div class="card">
                <p>
                    A major goal of Perseus is to provide an environment where developers can
                    create their own drivers.
                </p>
                <p class="mt-1">
                    The long-term idea is to make hardware support <strong>modular</strong>
                    rather than tightly coupled to the entire kernel.
                </p>
            </div>
        </section>

        <!-- ─── ROADMAP ─── -->
        <section>
            <h2 class="section-title icon-green"><i class="fas fa-map-signs"></i> Roadmap</h2>
            <div class="card">
                <p>There is no fixed roadmap yet. The current development direction looks approximately like this:</p>

                <div class="roadmap-grid">
                    <div class="roadmap-item"><span class="checkbox pending">☐</span> <span class="label-pending">16-bit bootloader</span></div>
                    <div class="roadmap-item"><span class="checkbox pending">☐</span> <span class="label-pending">Kernel loading</span></div>
                    <div class="roadmap-item"><span class="checkbox pending">☐</span> <span class="label-pending">16-bit kernel</span></div>
                    <div class="roadmap-item"><span class="checkbox pending">☐</span> <span class="label-pending">Basic memory management</span></div>
                    <div class="roadmap-item"><span class="checkbox pending">☐</span> <span class="label-pending">Basic I/O</span></div>
                    <div class="roadmap-item"><span class="checkbox pending">☐</span> <span class="label-pending">Enter protected mode</span></div>
                    <div class="roadmap-item"><span class="checkbox pending">☐</span> <span class="label-pending">32-bit kernel</span></div>
                    <div class="roadmap-item"><span class="checkbox pending">☐</span> <span class="label-pending">Shell</span></div>
                    <div class="roadmap-item"><span class="checkbox pending">☐</span> <span class="label-pending">Disk access</span></div>
                    <div class="roadmap-item"><span class="checkbox pending">☐</span> <span class="label-pending">Filesystem support</span></div>
                    <div class="roadmap-item"><span class="checkbox pending">☐</span> <span class="label-pending">FAT32 / EXT4</span></div>
                    <div class="roadmap-item"><span class="checkbox pending">☐</span> <span class="label-pending">Driver system</span></div>
                    <div class="roadmap-item"><span class="checkbox pending">☐</span> <span class="label-pending">User programs</span></div>
                    <div class="roadmap-item"><span class="checkbox pending">☐</span> <span class="label-pending">C integration</span></div>
                    <div class="roadmap-item"><span class="checkbox pending">☐</span> <span class="label-pending">32-bit LTS</span></div>
                    <div class="roadmap-item"><span class="checkbox pending">☐</span> <span class="label-pending">64-bit support</span></div>
                    <div class="roadmap-item" style="grid-column: 1 / -1;"><span class="checkbox pending">☐</span> <span class="label-pending">Full user-oriented OS</span></div>
                </div>

                <p class="mt-1" style="color: var(--text-muted); font-size: 0.9rem;">The roadmap will change as development progresses.</p>
            </div>
        </section>

        <!-- ─── RELEASES ─── -->
        <section>
            <h2 class="section-title"><i class="fas fa-tags"></i> Releases</h2>
            <div class="card">
                <p>
                    Official builds are planned to be distributed as <strong>.iso</strong> images
                    through the project's GitHub repository.
                </p>
                <p class="mt-1">Development builds may be unstable and should only be used for testing.</p>
            </div>
        </section>

        <!-- ─── CONTRIBUTING ─── -->
        <section>
            <h2 class="section-title icon-purple"><i class="fas fa-handshake"></i> Contributing</h2>
            <div class="card">
                <p>Perseus is intended to be an open-source project.</p>
                <p class="mt-1">
                    Contribution guidelines will be added once the project reaches a stage where
                    external contributions become practical.
                </p>
                <p class="mt-1">Future documentation may include:</p>
                <ul>
                    <li>Contribution guidelines</li>
                    <li>Source tree structure</li>
                    <li>Coding style</li>
                    <li>Pull request requirements</li>
                    <li>Driver development documentation</li>
                    <li>Kernel development documentation</li>
                </ul>
            </div>
        </section>

        <!-- ─── LICENSE ─── -->
        <section>
            <h2 class="section-title icon-green"><i class="fas fa-balance-scale"></i> License</h2>
            <div class="card">
                <p>
                    Perseus is licensed under the <strong>Apache License 2.0</strong>.
                </p>
                <p class="mt-1">You are free to:</p>
                <ul>
                    <li>Use the project privately</li>
                    <li>Use it commercially</li>
                    <li>Modify the source code</li>
                    <li>Redistribute the original or modified version</li>
                    <li>Create derivative works</li>
                    <li>Use the code in proprietary projects</li>
                </ul>
                <p class="mt-1">When redistributing the project, you must:</p>
                <ul>
                    <li>Include a copy of the Apache License 2.0</li>
                    <li>Preserve applicable copyright notices</li>
                    <li>Clearly indicate modified files</li>
                    <li>Follow the terms of the license</li>
                </ul>
                <div class="alert alert-info mt-1">
                    <strong>📄</strong> The software is provided without warranty.
                    The complete license text is available in <strong>LICENSE</strong>.
                </div>
            </div>
        </section>

        <!-- ─── AUTHOR ─── -->
        <section>
            <h2 class="section-title"><i class="fas fa-user-astronaut"></i> Author</h2>
            <div class="card">
                <p><strong>HighwayToHell-git</strong> &nbsp;·&nbsp; Daniil</p>
                <p class="mt-1">
                    <i class="fab fa-telegram" style="color: var(--accent-cyan);"></i>
                    Telegram: <a href="https://t.me/daniil_21_36" target="_blank">@daniil_21_36</a>
                </p>
            </div>
        </section>

        <!-- ─── README NOTE ─── -->
        <section>
            <h2 class="section-title icon-orange"><i class="fas fa-pen-fancy"></i> README</h2>
            <div class="card">
                <p>
                    This README was initially written by ChatGPT based on the project's description
                    and development plans provided by the author.
                </p>
            </div>
        </section>

        <!-- ─── DISCLAIMER ─── -->
        <section>
            <h2 class="section-title icon-red" style="--accent-red: #f87171;"><i class="fas fa-exclamation-triangle" style="color: var(--accent-red);"></i> Disclaimer</h2>
            <div class="card">
                <div class="alert" style="border-left-color: var(--accent-orange); background: rgba(251, 191, 36, 0.06);">
                    <strong>⚠️ Perseus is an experimental operating system project.</strong>
                    <br />
                    Early versions are not intended for production use or for storing important data.
                    <br />
                    When experimenting with bootloaders, kernels, disks, and filesystems, use a
                    virtual machine or dedicated test hardware.
                </div>
            </div>
        </section>

        <!-- ─── FOOTER ─── -->
        <hr class="footer-divider" />

        <div class="footer-note">
            ⚔️ Perseus &nbsp;·&nbsp; From bootloader to user OS.
            <br />
            Built from scratch. One instruction at a time.
            <br />
            <span style="font-size: 0.8rem; color: var(--text-muted); margin-top: 0.3rem; display: inline-block;">
                <i class="fas fa-code"></i> with <i class="fas fa-heart" style="color: var(--accent-red);"></i> by HighwayToHell-git
            </span>
        </div>

    </div>
    <!-- /.container -->
</body>
</html>