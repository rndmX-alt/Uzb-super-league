<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Uzbekistan Super League – Official System 2026</title>
    <style>
        :root {
            --bg-dark: #0b0d17;
            --bg-panel: #15192b;
            --primary: #00f0ff;
            --secondary: #2d34e6;
            --accent: #ff0055;
            --text-main: #ffffff;
            --text-dim: #8b9bb4;
            --rank-s: #ffd700;
            --rank-a: #bf00ff;
            --rank-b: #00ff66;
            --rank-c: #e0e0e0;
            --border: 1px solid rgba(0, 240, 255, 0.2);
            --font-main: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { background-color: var(--bg-dark); color: var(--text-main); font-family: var(--font-main); overflow-x: hidden; padding-bottom: 50px; }
        
        h1, h2, h3 { text-transform: uppercase; letter-spacing: 2px; }
        .neon-text { text-shadow: 0 0 10px var(--primary); color: var(--primary); }
        .hidden { display: none !important; }
        .btn { cursor: pointer; border: none; outline: none; padding: 10px 20px; font-weight: bold; text-transform: uppercase; transition: 0.3s; clip-path: polygon(10px 0, 100% 0, 100% calc(100% - 10px), calc(100% - 10px) 100%, 0 100%, 0 10px); }
        .btn-primary { background: var(--primary); color: #000; }
        .btn-primary:hover { background: #fff; box-shadow: 0 0 15px var(--primary); }
        .btn-danger { background: var(--accent); color: #fff; }
        .btn-warning { background: var(--rank-s); color: #000; }
        
        .flex { display: flex; gap: 10px; flex-wrap: wrap; }
        .grid { display: grid; gap: 20px; }
        
        nav { background: rgba(11, 13, 23, 0.95); border-bottom: 1px solid var(--primary); padding: 15px 20px; position: sticky; top: 0; z-index: 100; display: flex; justify-content: space-between; align-items: center; backdrop-filter: blur(5px); }
        .nav-links { display: flex; align-items: center; flex-wrap: wrap; gap: 5px; }
        .nav-links button { background: transparent; color: var(--text-dim); border: none; font-size: 0.8rem; cursor: pointer; text-transform: uppercase; transition: 0.2s; padding: 5px 10px; }
        .nav-links button:hover, .nav-links button.active { color: var(--primary); text-shadow: 0 0 8px var(--primary); }
        .logo { font-size: 1.2rem; font-weight: 900; font-style: italic; border-left: 4px solid var(--accent); padding-left: 10px; }
        
        #adminBtn { border: 1px solid var(--accent); color: var(--accent); border-radius: 4px; margin-left: 10px; }
        #adminBtn:hover { background: var(--accent); color: white; box-shadow: 0 0 10px var(--accent); }

        main { padding: 30px 20px; max-width: 1400px; margin: 0 auto; min-height: 80vh; }
        .section { animation: fadeIn 0.5s ease; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

        input, select { background: rgba(0,0,0,0.3); border: 1px solid var(--primary); color: #fff; padding: 10px; width: 100%; outline: none; margin-bottom: 10px; }
        input:focus { box-shadow: 0 0 10px rgba(0, 240, 255, 0.3); }

        .card { background: var(--bg-panel); border: var(--border); padding: 20px; position: relative; }
        .card::before { content: ''; position: absolute; top: 0; left: 0; width: 4px; height: 100%; background: var(--primary); }

        table { width: 100%; border-collapse: collapse; margin-top: 20px; }
        th { text-align: left; padding: 15px; background: rgba(0, 240, 255, 0.1); color: var(--primary); text-transform: uppercase; font-size: 0.8rem; }
        td { padding: 15px; border-bottom: 1px solid rgba(255,255,255,0.05); }
        tr:hover td { background: rgba(255,255,255,0.02); }

        .admin-only { display: none; }
        body.is-admin .admin-only { display: block; }
        .admin-controls { margin-bottom: 20px; padding: 15px; border: 1px dashed var(--accent); background: rgba(255, 0, 85, 0.05); }

        .rank-s-text { color: var(--rank-s); font-weight: bold; text-shadow: 0 0 5px var(--rank-s); }
        .rank-a-text { color: var(--rank-a); font-weight: bold; }
        .rank-b-text { color: var(--rank-b); }
        .rank-c-text { color: var(--text-dim); }

        .modal { position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.8); z-index: 1000; display: flex; justify-content: center; align-items: center; }
        .modal-content { background: var(--bg-panel); padding: 30px; border: 1px solid var(--primary); max-width: 800px; width: 95%; max-height: 90vh; overflow-y: auto; box-shadow: 0 0 30px rgba(0, 240, 255, 0.2); }
        
        .match-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 20px; }
        .match-card { display: flex; flex-direction: column; align-items: center; padding: 15px; border: 1px solid #333; background: #0f121e; }
        .score-board { font-size: 2rem; font-weight: bold; margin: 10px 0; color: var(--primary); }

        .profile-header { display: flex; align-items: center; justify-content: space-between; margin-bottom: 20px; flex-wrap: wrap; gap: 10px; }
        .hype-btn { background: linear-gradient(45deg, #ff4d00, #ff9900); color: #fff; border: none; padding: 10px 20px; font-weight: bold; cursor: pointer; clip-path: polygon(10px 0, 100% 0, 100% calc(100% - 10px), calc(100% - 10px) 100%, 0 100%, 0 10px); display: flex; align-items: center; gap: 5px; }
        .compare-val { font-family: monospace; font-size: 1.1rem; }
        .compare-val.winner { color: var(--rank-b); font-weight: bold; text-shadow: 0 0 5px var(--rank-b); }

        .awards-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; }
        .award-card { text-align: center; border: 1px solid var(--accent); background: linear-gradient(180deg, rgba(255,0,85,0.1), transparent); }
        .award-icon { font-size: 3rem; margin-bottom: 10px; display: block; }
        .award-title { color: var(--accent); font-size: 0.9rem; margin-bottom: 5px; }
        .award-winner { font-size: 1.2rem; font-weight: bold; color: #fff; }
        .money { color: var(--rank-s); font-family: monospace; }
        
        .chk-container { display: flex; gap: 10px; align-items: center; font-size: 0.8rem; color: #aaa; }
        .chk-container input { width: auto; margin: 0; }
        .history-log { font-size: 0.8rem; color: #888; border-left: 2px solid #333; padding-left: 10px; margin-top: 5px; }
        .rank-list-item { display: flex; align-items: center; justify-content: space-between; padding: 10px; border-bottom: 1px solid rgba(255,255,255,0.05); }
        .rank-1 { border-left: 3px solid var(--rank-s); background: linear-gradient(90deg, rgba(255, 215, 0, 0.1), transparent); }
        .rank-2 { border-left: 3px solid #c0c0c0; }
        .rank-3 { border-left: 3px solid #cd7f32; }

        .notification { position: fixed; bottom: 20px; right: 20px; background: var(--primary); color: #000; padding: 15px 25px; font-weight: bold; z-index: 2000; display: none; }
    </style>
</head>
<body>

<nav>
    <div class="logo">UZB SL <span style="color:var(--primary)" id="season-display">2026</span></div>
    <div class="nav-links">
        <button onclick="app.nav('registry')">Registry</button>
        <button onclick="app.nav('match-center')">Match Center</button>
        <button onclick="app.nav('results')">Results</button>
        <button onclick="app.nav('standings')">Standings</button>
        <button onclick="app.nav('leaderboard')">Players</button>
        <button onclick="app.nav('awards')">Awards</button>
        <button onclick="app.toggleAdmin()" id="adminBtn">ADMIN LOGIN</button>
    </div>
</nav>

<main id="app-container"></main>

<div id="modal-overlay" class="modal hidden">
    <div class="modal-content" id="modal-body"></div>
</div>

<div id="notification" class="notification">Action Successful</div>

<script>
/** * UZBEKISTAN SUPER LEAGUE - FIXED COMPLETE VERSION 
 */

const DB_KEY = 'usl_data_2026_fixed_v1';
const ADMIN_PASS = 'Bojboj2009!*';

const initialState = {
    seasonName: "2026 Season",
    teams: [],
    players: [],
    matches: [],
    settings: { isAdmin: false }
};

const db = {
    get: () => {
        try {
            const data = localStorage.getItem(DB_KEY);
            return data ? JSON.parse(data) : initialState;
        } catch(e) { return initialState; }
    },
    save: (data) => {
        localStorage.setItem(DB_KEY, JSON.stringify(data));
        window.app.refresh();
    },
    update: (cb) => {
        const data = db.get();
        const newData = cb(data);
        db.save(newData);
    }
};

const util = {
    uuid: () => Date.now().toString(36) + Math.random().toString(36).substr(2),
    notify: (msg) => {
        const el = document.getElementById('notification');
        el.innerText = msg;
        el.style.display = 'block';
        setTimeout(() => el.style.display = 'none', 3000);
    },
    formatMoney: (amount) => '$' + amount.toLocaleString(),
    getRank: (val, type) => {
        if(type === 'goals') return val >= 3.5 ? 'S' : val >= 2.5 ? 'A' : val >= 1.5 ? 'B' : 'C';
        if(type === 'saves') return val >= 15 ? 'S' : val >= 10 ? 'A' : val >= 5 ? 'B' : 'C';
        if(type === 'tackles') return val >= 10 ? 'S' : val >= 7 ? 'A' : val >= 5 ? 'B' : 'C';
        return 'C';
    },
    getClass: (rank) => `rank-${rank.toLowerCase()}-text`
};

// --- APP LOGIC ---
window.app = {
    currentView: 'registry',
    sortBy: 'goals',
    selectedPlayerId: null,

    init: () => {
        if (!localStorage.getItem(DB_KEY)) db.save(initialState);
        window.app.render();
    },

    refresh: () => { window.app.render(); },

    nav: (view) => {
        window.app.currentView = view;
        document.querySelectorAll('.nav-links button').forEach(b => {
            if (b.id !== 'adminBtn') b.classList.remove('active');
        });
        const btns = Array.from(document.querySelectorAll('.nav-links button'));
        const activeBtn = btns.find(b => b.getAttribute('onclick')?.includes(view));
        if(activeBtn) activeBtn.classList.add('active');
        window.app.render();
    },

    toggleAdmin: () => {
        const data = db.get();
        if(data.settings.isAdmin) {
            data.settings.isAdmin = false;
            db.save(data);
            util.notify("Logged out");
        } else {
            // Using slight timeout to ensure prompt displays in some browsers
            setTimeout(() => {
                const pass = prompt("ENTER ADMIN PASSWORD:");
                if(pass === ADMIN_PASS) {
                    data.settings.isAdmin = true;
                    db.save(data);
                    util.notify("ADMIN UNLOCKED");
                } else if (pass !== null) {
                    alert("ACCESS DENIED");
                }
            }, 50);
        }
    },

    render: () => {
        const data = db.get();
        const container = document.getElementById('app-container');
        document.body.className = data.settings.isAdmin ? 'is-admin' : '';
        document.getElementById('season-display').innerText = data.seasonName;
        
        const adminBtn = document.getElementById('adminBtn');
        if (data.settings.isAdmin) {
            adminBtn.innerText = "LOGOUT ADMIN";
            adminBtn.style.borderColor = "var(--primary)";
            adminBtn.style.color = "var(--primary)";
        } else {
            adminBtn.innerText = "ADMIN LOGIN";
            adminBtn.style.borderColor = "var(--accent)";
            adminBtn.style.color = "var(--accent)";
        }

        if(window.app.currentView === 'registry') renderRegistry(container, data);
        else if(window.app.currentView === 'match-center') renderMatchCenter(container, data);
        else if(window.app.currentView === 'results') renderResults(container, data);
        else if(window.app.currentView === 'standings') renderStandings(container, data);
        else if(window.app.currentView === 'leaderboard') renderLeaderboard(container, data);
        else if(window.app.currentView === 'awards') renderAwards(container, data);
        else if(window.app.currentView === 'profile') renderProfile(container, data);
    },

    openProfile: (pid) => {
        window.app.selectedPlayerId = pid;
        window.app.nav('profile');
    },

    renderCompare: (oppId, myId) => {
        if(!oppId) { document.getElementById('compareResult').innerHTML = ''; return; }
        const data = db.get();
        const allStats = calculatePlayerStats(data);
        const me = allStats.find(p => p.id === myId);
        const opp = allStats.find(p => p.id === oppId);
        const row = (label, v1, v2) => `
            <div style="display:flex; justify-content:space-between; border-bottom:1px solid #333; padding:10px 0;">
                <span class="${v1 > v2 ? 'compare-val winner' : 'compare-val'}">${v1}</span>
                <span style="color:#888; font-size:0.8rem;">${label}</span>
                <span class="${v2 > v1 ? 'compare-val winner' : 'compare-val'}">${v2}</span>
            </div>`;
        document.getElementById('compareResult').innerHTML = `
            <div style="text-align:center; margin-bottom:10px;">
                <span style="font-weight:bold; color:${me.teamColor}">${me.name}</span> VS 
                <span style="font-weight:bold; color:${opp.teamColor}">${opp.name}</span>
            </div>
            ${row('GOALS', me.goals, opp.goals)}
            ${row('ASSISTS', me.assists, opp.assists)}
            ${row('SAVES', me.saves, opp.saves)}
            ${row('TACKLES', me.tackles, opp.tackles)}
            ${row('VALUE', util.formatMoney(me.marketValue), util.formatMoney(opp.marketValue))}
        `;
    }
};

// --- VIEW FUNCTIONS ---
function renderRegistry(root, data) {
    root.innerHTML = `
        <div class="section">
            <h2 class="neon-text">Team & Player Registry</h2>
            <div class="admin-controls admin-only">
                <h3>Admin Tools</h3>
                <div class="flex" style="margin-top:10px;">
                    <input type="text" id="newTeamName" placeholder="Team Name" style="width:200px;">
                    <input type="color" id="newTeamColor" value="#00f0ff" style="width:50px; height:42px; padding:0;">
                    <button class="btn btn-primary" onclick="actions.addTeam()">Add Team</button>
                    <button class="btn btn-warning" onclick="modals.openTransferMarket()">Transfer Market</button>
                    <button class="btn btn-danger" onclick="modals.openSeasonControl()">Season Control</button>
                </div>
            </div>
            <div class="grid" style="grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));">
                ${data.teams.map(t => `
                    <div class="card" style="border-color:${t.color}">
                        <div style="display:flex; justify-content:space-between; color:${t.color}; margin-bottom:10px;">
                            <h3 style="font-weight:900;">${t.name}</h3>
                            ${data.settings.isAdmin ? `<button class="btn btn-danger" style="padding:2px 5px; font-size:0.7rem;" onclick="actions.deleteTeam('${t.id}')">X</button>` : ''}
                        </div>
                        <ul style="list-style:none; margin-bottom:15px;">
                            ${data.players.filter(p => p.teamId === t.id).map(p => `
                                <li style="padding:5px 0; border-bottom:1px solid rgba(255,255,255,0.1); display:flex; justify-content:space-between;">
                                    <div>
                                        <span style="color:${t.color}">${p.name}</span>
                                        ${p.loanStatus ? '<span style="font-size:0.7rem; background:#ff9900; color:black; padding:0 3px; border-radius:3px;">LOAN</span>' : ''}
                                    </div>
                                    ${data.settings.isAdmin ? `<button onclick="actions.deletePlayer('${p.id}')" style="background:none; border:none; color:#555; cursor:pointer;">x</button>` : ''}
                                </li>
                            `).join('')}
                        </ul>
                        <div class="admin-only">
                            <div class="flex">
                                <input type="text" id="p-name-${t.id}" placeholder="Player Name" style="font-size:0.8rem; margin:0;">
                                <button class="btn btn-primary" style="padding:5px 10px;" onclick="actions.addPlayer('${t.id}')">+</button>
                            </div>
                        </div>
                    </div>
                `).join('')}
            </div>
            ${data.teams.length === 0 ? '<div class="card text-center" style="margin-top:20px;"><h3>SYSTEM EMPTY</h3><p>Please login as ADMIN to add teams.</p></div>' : ''}
        </div>
    `;
}

function renderMatchCenter(root, data) {
    root.innerHTML = `
        <div class="section">
            <h2 class="neon-text">EGOIST GRADING SYSTEM</h2>
            <p style="color:var(--text-dim); margin-bottom:20px;">Players are graded based on stats PER LEG (calculated only for legs played).</p>
            <div class="grid" style="grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));">
                <div class="card"><h3 class="rank-s-text">S-RANK</h3><ul><li>3.5 Goals / Leg</li><li>15 Saves / Leg</li><li>10 Tackles / Leg</li></ul></div>
                <div class="card"><h3 class="rank-a-text">A-RANK</h3><ul><li>2.5 Goals / Leg</li><li>10 Saves / Leg</li><li>7 Tackles / Leg</li></ul></div>
                <div class="card"><h3 class="rank-b-text">B-RANK</h3><ul><li>1.5 Goals / Leg</li><li>5 Saves / Leg</li><li>5 Tackles / Leg</li></ul></div>
                <div class="card"><h3 class="rank-c-text">C-RANK</h3><p>Below average metrics.</p></div>
            </div>
        </div>
    `;
}

function renderResults(root, data) {
    root.innerHTML = `
        <div class="section">
            <h2 class="neon-text">Match Results</h2>
            <div class="admin-controls admin-only">
                <button class="btn btn-primary" onclick="modals.openMatchCreation()">+ RECORD NEW MATCH</button>
            </div>
            <div class="match-grid">
                ${data.matches.map(m => {
                    const tA = data.teams.find(t => t.id === m.teamAId) || {name:'?', color:'#fff'};
                    const tB = data.teams.find(t => t.id === m.teamBId) || {name:'?', color:'#fff'};
                    const mvp = data.players.find(p => p.id === m.mvpId);
                    const motm = data.players.find(p => p.id === m.motmId);
                    return `
                    <div class="match-card">
                        <div style="width:100%; display:flex; justify-content:space-between; align-items:center; margin-bottom:10px;">
                            <span style="color:${tA.color}; font-weight:bold;">${tA.name}</span>
                            <span style="font-size:0.8rem; color:#666;">VS</span>
                            <span style="color:${tB.color}; font-weight:bold;">${tB.name}</span>
                        </div>
                        <div class="score-board">${parseInt(m.leg1ScoreA)+parseInt(m.leg2ScoreA)} - ${parseInt(m.leg1ScoreB)+parseInt(m.leg2ScoreB)}</div>
                        <div style="font-size:0.8rem; color:#888; margin-bottom:10px;">(L1: ${m.leg1ScoreA}-${m.leg1ScoreB}, L2: ${m.leg2ScoreA}-${m.leg2ScoreB})</div>
                        <div style="width:100%; border-top:1px solid #333; padding-top:10px; font-size:0.8rem;">
                            <div><span class="neon-text">MVP:</span> ${mvp ? mvp.name : 'N/A'}</div>
                            <div><span style="color:var(--rank-s)">MOTM:</span> ${motm ? motm.name : 'N/A'}</div>
                        </div>
                        ${data.settings.isAdmin ? `<button onclick="actions.deleteMatch('${m.id}')" style="margin-top:10px; background:maroon; border:none; color:white; font-size:0.7rem; width:100%;">DELETE MATCH</button>` : ''}
                    </div>`;
                }).join('')}
            </div>
            ${data.matches.length === 0 ? '<p style="color:#666; margin-top:20px;">No matches recorded yet.</p>' : ''}
        </div>
    `;
}

function renderStandings(root, data) {
    const tableData = data.teams.map(team => {
        let stats = { mp:0, w:0, d:0, l:0, gf:0, ga:0, pts:0 };
        data.matches.forEach(m => {
            if(m.teamAId !== team.id && m.teamBId !== team.id) return;
            stats.mp++;
            const isA = m.teamAId === team.id;
            const myScore = isA ? (parseInt(m.leg1ScoreA) + parseInt(m.leg2ScoreA)) : (parseInt(m.leg1ScoreB) + parseInt(m.leg2ScoreB));
            const oppScore = isA ? (parseInt(m.leg1ScoreB) + parseInt(m.leg2ScoreB)) : (parseInt(m.leg1ScoreA) + parseInt(m.leg2ScoreA));
            stats.gf += myScore; stats.ga += oppScore;
            if (myScore > oppScore) { stats.w++; stats.pts += 3; }
            else if (myScore < oppScore) { stats.l++; }
            else { stats.d++; stats.pts -= 1; }
        });
        return { ...team, ...stats, gd: stats.gf - stats.ga };
    }).sort((a,b) => b.pts - a.pts || b.gd - a.gd);

    root.innerHTML = `
        <div class="section">
            <h2 class="neon-text">League Standings</h2>
            <table>
                <thead><tr><th>Rk</th><th>Team</th><th>MP</th><th>W</th><th>D</th><th>L</th><th>GD</th><th>PTS</th></tr></thead>
                <tbody>
                    ${tableData.map((t, idx) => `
                        <tr><td>${idx + 1}</td><td style="color:${t.color}; font-weight:bold;">${t.name}</td><td>${t.mp}</td><td>${t.w}</td><td>${t.d}</td><td>${t.l}</td><td>${t.gd > 0 ? '+'+t.gd : t.gd}</td><td class="neon-text">${t.pts}</td></tr>
                    `).join('')}
                </tbody>
            </table>
        </div>
    `;
}

function renderLeaderboard(root, data) {
    const stats = calculatePlayerStats(data);
    const sortBy = window.app.sortBy;
    stats.sort((a,b) => b[sortBy] - a[sortBy]);
    root.innerHTML = `
        <div class="section">
            <h2 class="neon-text">Player Leaderboard</h2>
            <div class="flex" style="margin-bottom:15px;">
                ${['goals','assists','saves','tackles'].map(s => `<button class="btn ${sortBy===s?'btn-primary':''}" onclick="window.app.sortBy='${s}'; window.app.render()">${s}</button>`).join('')}
            </div>
            <table>
                <thead><tr><th>Rk</th><th>Player</th><th>Team</th><th>${sortBy.toUpperCase()}</th></tr></thead>
                <tbody>
                    ${stats.map((p, idx) => `
                        <tr onclick="window.app.openProfile('${p.id}')" style="cursor:pointer;">
                            <td>${idx + 1}</td><td>${p.name}</td><td style="color:${p.teamColor}">${p.teamName}</td><td class="neon-text">${p[sortBy]}</td>
                        </tr>
                    `).join('')}
                </tbody>
            </table>
        </div>
    `;
}

function renderProfile(root, data) {
    const pid = window.app.selectedPlayerId;
    const player = data.players.find(p => p.id === pid);
    if(!player) return window.app.nav('leaderboard');
    const team = data.teams.find(t => t.id === player.teamId);
    const pStats = calculatePlayerStats(data).find(p => p.id === pid);
    const legs = pStats.legsPlayed || 1; 
    const av = (val) => (val / legs).toFixed(2);
    const hasVoted = localStorage.getItem(`voted_${pid}`);

    root.innerHTML = `
        <div class="section">
            <button onclick="window.app.nav('leaderboard')" style="margin-bottom:20px; background:none; border:1px solid #333; color:#fff; padding:5px 10px;">&larr; BACK</button>
            <div class="profile-header">
                <div><h1 style="color:${team.color};">${player.name}</h1><h3 style="color:#666;">${team.name} ${player.loanStatus ? '(LOAN)' : ''}</h3></div>
                <button class="hype-btn" onclick="actions.hypePlayer('${pid}')" ${hasVoted ? 'disabled style="opacity:0.5"' : ''}>🔥 HYPE <span>${player.hype || 0}</span></button>
            </div>
            ${player.transferHistory ? `<div style="margin-bottom:20px;"><h4>Transfer History</h4>${player.transferHistory.map(h => `<div class="history-log">${h}</div>`).join('')}</div>` : ''}
            <div class="grid" style="grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));">
                <div class="card">
                    <h3>LEG ANALYSIS (${pStats.legsPlayed} Legs)</h3>
                    <div style="margin-top:15px; display:grid; grid-template-columns:1fr 1fr; gap:15px;">
                        <div><span style="display:block; font-size:0.8rem; color:#888;">GOALS/LEG</span><span class="${util.getClass(util.getRank(av(pStats.goals), 'goals'))}" style="font-size:1.5rem;">${av(pStats.goals)}</span></div>
                        <div><span style="display:block; font-size:0.8rem; color:#888;">ASSISTS/LEG</span><span class="rank-c-text" style="font-size:1.5rem;">${av(pStats.assists)}</span></div>
                        <div><span style="display:block; font-size:0.8rem; color:#888;">SAVES/LEG</span><span class="${util.getClass(util.getRank(av(pStats.saves), 'saves'))}" style="font-size:1.5rem;">${av(pStats.saves)}</span></div>
                        <div><span style="display:block; font-size:0.8rem; color:#888;">TACKLES/LEG</span><span class="${util.getClass(util.getRank(av(pStats.tackles), 'tackles'))}" style="font-size:1.5rem;">${av(pStats.tackles)}</span></div>
                    </div>
                </div>
                <div class="card"><h3>MARKET VALUE</h3><h2 class="neon-text" style="margin-top:20px; font-size:2rem;">${util.formatMoney(pStats.marketValue)}</h2></div>
            </div>
            <div class="card" style="margin-top:20px;">
                <div class="flex" style="justify-content:space-between; align-items:center;"><h3>⚖️ COMPARE</h3><select id="compareSelect" onchange="window.app.renderCompare(this.value, '${pid}')" style="width:200px;"><option value="">Select Player...</option>${data.players.filter(p => p.id !== pid).map(p => `<option value="${p.id}">${p.name}</option>`).join('')}</select></div>
                <div id="compareResult" style="margin-top:15px;"></div>
            </div>
            <div class="card" style="margin-top:20px;">
                <h3>MATCH HISTORY</h3>
                 ${pStats.matchLogs.map(m => `
                    <div style="border-bottom:1px solid #333; padding:10px 0; font-size:0.9rem;">
                       <span style="color:#888;">vs</span> <span style="font-weight:bold;">${m.opponentName}</span>
                       <span style="float:right;">${m.goals}G ${m.assists}A ${m.playedLeg1?'<span style="color:var(--primary); font-size:0.7rem; border:1px solid var(--primary); padding:1px 4px;">L1</span>':''} ${m.playedLeg2?'<span style="color:var(--primary); font-size:0.7rem; border:1px solid var(--primary); padding:1px 4px;">L2</span>':''}</span>
                    </div>`).join('')}
            </div>
        </div>`;
}

function renderAwards(root, data) {
    const stats = calculatePlayerStats(data);
    const topScorer = [...stats].sort((a,b) => b.goals - a.goals)[0];
    const topPlaymaker = [...stats].sort((a,b) => b.assists - a.assists)[0];
    const topGlove = [...stats].sort((a,b) => b.saves - a.saves)[0];
    const topDefender = [...stats].sort((a,b) => b.tackles - a.tackles)[0];
    const topValue = [...stats].sort((a,b) => b.marketValue - a.marketValue)[0];
    const bestDuo = calculateDuos(data)[0];

    // Ballon d'Or
    const teamStandings = data.teams.map(team => {
        let pts = 0;
        data.matches.forEach(m => {
            if(m.teamAId !== team.id && m.teamBId !== team.id) return;
            const isA = m.teamAId === team.id;
            const myScore = isA ? (parseInt(m.leg1ScoreA)+parseInt(m.leg2ScoreA)) : (parseInt(m.leg1ScoreB)+parseInt(m.leg2ScoreB));
            const oppScore = isA ? (parseInt(m.leg1ScoreB)+parseInt(m.leg2ScoreB)) : (parseInt(m.leg1ScoreA)+parseInt(m.leg2ScoreA));
            pts += (myScore > oppScore) ? 3 : (myScore < oppScore ? 0 : -1);
        });
        return { id: team.id, pts };
    }).sort((a,b) => b.pts - a.pts);

    const ballonList = stats.map(p => {
        let pts = (p.goals * 5) + (p.assists * 5) + (p.saves * 1) + (p.tackles * 0.2);
        pts += (p.mvpCount + p.motmCount) * 10;
        const teamRank = teamStandings.findIndex(t => t.id === p.teamId);
        if(teamRank === 0) pts += 20;
        if(teamRank === 1) pts += 10;
        if(teamRank === 2) pts += 5;
        if(p.id === topScorer?.id) pts += 20;
        else if(p.id === topPlaymaker?.id) pts += 20;
        else if(p.id === topGlove?.id) pts += 20;
        else if(p.id === topDefender?.id) pts += 20;
        return { ...p, bPoints: pts };
    }).sort((a,b) => b.bPoints - a.bPoints).slice(0, 10);

    const card = (t, i, p, s) => `<div class="card award-card"><span class="award-icon">${i}</span><div class="award-title">${t}</div>${p?`<div class="award-winner" style="color:${p.teamColor}">${p.name}</div><div style="font-size:0.8rem; color:#888;">${p.teamName}</div><div class="neon-text">${s}</div>`:'<div style="color:#666">No Data</div>'}</div>`;
    
    root.innerHTML = `
        <div class="section">
            <h2 class="neon-text" style="text-align:center; margin-bottom:30px;">Season Awards</h2>
            <div class="awards-grid">
                ${card("GOLDEN BOOT", "👟", topScorer, (topScorer?.goals||0)+" Goals")}
                ${card("PLAYMAKER", "🎯", topPlaymaker, (topPlaymaker?.assists||0)+" Assists")}
                ${card("GOLDEN GLOVES", "🧤", topGlove, (topGlove?.saves||0)+" Saves")}
                ${card("BEST DEFENDER", "🛡️", topDefender, (topDefender?.tackles||0)+" Tackles")}
                <div class="card award-card"><span class="award-icon">🧠</span><div class="award-title">BEST DUO</div>${bestDuo?`<div class="award-winner" style="font-size:1rem;">${bestDuo.p1Name} + ${bestDuo.p2Name}</div><div style="font-size:0.8rem; color:#888;">${bestDuo.teamName}</div><div class="neon-text">${bestDuo.total.toFixed(1)} (G+A)</div>`:'<div style="color:#666">No Data</div>'}</div>
            </div>
            <div style="margin-top:30px; display:grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap:20px;">
                <div class="card" style="border-color:gold;"><h3 style="color:gold; text-align:center;">🏆 BALLON D'OR TOP 10</h3><div style="margin-top:15px;">${ballonList.map((p,i)=>`<div class="rank-list-item rank-${i+1}"><div><span style="font-weight:bold; margin-right:10px;">#${i+1}</span><span style="color:${p.teamColor}; font-weight:bold;">${p.name}</span><div style="font-size:0.7rem; color:#888; margin-left:30px;">${p.teamName}</div></div><div class="neon-text">${p.bPoints.toFixed(1)}</div></div>`).join('')}</div></div>
                <div class="card" style="border-color:var(--rank-s);"><h3 style="color:var(--rank-s); text-align:center;">💰 MOST VALUABLE</h3>${topValue?`<div style="text-align:center; margin-top:15px;"><h1 style="color:${topValue.teamColor}; font-size:2.5rem;">${topValue.name}</h1><p class="money">${util.formatMoney(topValue.marketValue)}</p></div>`:''}</div>
            </div>
        </div>`;
}

// --- CALCULATION HELPERS ---
function calculatePlayerStats(data) {
    return data.players.map(p => {
        const team = data.teams.find(t => t.id === p.teamId) || {name:'Unknown', color:'#fff'};
        let stats = { id: p.id, name: p.name, teamId: p.teamId, teamName: team.name, teamColor: team.color, hype: p.hype||0, goals:0, assists:0, saves:0, tackles:0, legsPlayed:0, mvpCount:0, motmCount:0, matchLogs:[] };
        
        data.matches.forEach(m => {
            const pMatch = m.playerStats.find(ps => ps.playerId === p.id);
            if(pMatch) {
                const playedL1 = pMatch.playedLeg1 !== false;
                const playedL2 = pMatch.playedLeg2 !== false;
                if(playedL1) stats.legsPlayed++;
                if(playedL2) stats.legsPlayed++;
                stats.goals += parseInt(pMatch.goals||0); stats.assists += parseInt(pMatch.assists||0);
                stats.saves += parseInt(pMatch.saves||0); stats.tackles += parseInt(pMatch.tackles||0);
                if(m.mvpId === p.id) stats.mvpCount++;
                if(m.motmId === p.id) stats.motmCount++;
                const oppId = m.teamAId === pMatch.teamId ? m.teamBId : m.teamAId;
                const oppName = (data.teams.find(t=>t.id===oppId) || {name:'?'}).name;
                stats.matchLogs.push({ ...pMatch, matchId: m.id, opponentName: oppName, playedLeg1: playedL1, playedLeg2: playedL2 });
            }
        });
        
        stats.marketValue = (stats.goals*2000000) + (stats.assists*1000000) + (stats.hype*100000) + (stats.saves*400000) + (stats.tackles*100000) + ((stats.mvpCount+stats.motmCount)*3000000);
        return stats;
    });
}

function calculateDuos(data) {
    const pairMap = {};
    data.matches.forEach(m => {
        const teamGroups = {};
        m.playerStats.forEach(p => { if(!teamGroups[p.teamId]) teamGroups[p.teamId]=[]; teamGroups[p.teamId].push(p); });
        Object.values(teamGroups).forEach(teamPlayers => {
            const processLeg = (players) => {
                for(let i=0; i<players.length; i++) {
                    for(let j=i+1; j<players.length; j++) {
                        const p1=players[i], p2=players[j];
                        const key = [p1.playerId, p2.playerId].sort().join('_');
                        if(!pairMap[key]) {
                            const pl1 = data.players.find(x => x.id === p1.playerId);
                            const pl2 = data.players.find(x => x.id === p2.playerId);
                            const tm = data.teams.find(t => t.id === p1.teamId);
                            if(pl1 && pl2 && tm) pairMap[key] = { total: 0, p1Name: pl1.name, p2Name: pl2.name, teamName: tm.name };
                        }
                        if(pairMap[key]) {
                             // Approximating contribution: (Total Match G+A) / (Legs Played). 
                             const p1Contrib = (parseInt(p1.goals)+parseInt(p1.assists)) / ((p1.playedLeg1?1:0) + (p1.playedLeg2?1:0));
                             const p2Contrib = (parseInt(p2.goals)+parseInt(p2.assists)) / ((p2.playedLeg1?1:0) + (p2.playedLeg2?1:0));
                             pairMap[key].total += (p1Contrib + p2Contrib);
                        }
                    }
                }
            };
            processLeg(teamPlayers.filter(p => p.playedLeg1 !== false));
            processLeg(teamPlayers.filter(p => p.playedLeg2 !== false));
        });
    });
    return Object.values(pairMap).sort((a,b) => b.total - a.total);
}

// --- ACTIONS & MODALS ---
window.actions = {
    addTeam: () => {
        const name = document.getElementById('newTeamName').value;
        const color = document.getElementById('newTeamColor').value;
        if(!name) return alert("Enter team name");
        db.update(data => { data.teams.push({ id: util.uuid(), name, color }); return data; });
        util.notify("Team Added");
    },
    deleteTeam: (id) => {
        if(!confirm("Delete Team? This deletes players too.")) return;
        db.update(data => { data.teams = data.teams.filter(t => t.id !== id); data.players = data.players.filter(p => p.teamId !== id); return data; });
        util.notify("Team Deleted");
    },
    addPlayer: (teamId) => {
        const name = document.getElementById(`p-name-${teamId}`).value;
        if(!name) return alert("Enter player name");
        db.update(data => { data.players.push({ id: util.uuid(), name, teamId, hype: 0, transferCount: 0, loanStatus: null, transferHistory: [] }); return data; });
        util.notify("Player Added");
    },
    deletePlayer: (id) => {
        if(!confirm("Delete Player?")) return;
        db.update(data => { data.players = data.players.filter(p => p.id !== id); return data; });
        util.notify("Player Deleted");
    },
    deleteMatch: (id) => {
        if(!confirm("Delete Match Result?")) return;
        db.update(data => { data.matches = data.matches.filter(m => m.id !== id); return data; });
        util.notify("Match Deleted");
    },
    hypePlayer: (pid) => {
        if(localStorage.getItem(`voted_${pid}`)) return alert("Already voted!");
        db.update(data => { const p = data.players.find(x => x.id === pid); if(p) p.hype = (p.hype||0)+1; return data; });
        localStorage.setItem(`voted_${pid}`, 'true');
        util.notify("HYPE ADDED (+ $100k)");
    },
    transferPlayer: () => {
        const pid = document.getElementById('tf-player').value;
        const tid = document.getElementById('tf-newteam').value;
        if(!pid || !tid) return alert("Select player and team");
        db.update(data => {
            const p = data.players.find(x => x.id === pid);
            const t = data.teams.find(x => x.id === tid);
            if((p.transferCount || 0) >= 2) return alert("Max 2 transfers reached."); 
            p.transferHistory = p.transferHistory || []; p.transferHistory.push(`Transferred to ${t.name}`);
            p.teamId = tid; p.transferCount = (p.transferCount||0)+1; p.loanStatus = null;
            return data;
        });
        util.notify("Transfer Complete"); window.modals.openTransferMarket();
    },
    loanPlayer: () => {
        const pid = document.getElementById('ln-player').value;
        const tid = document.getElementById('ln-newteam').value;
        if(!pid || !tid) return alert("Select player and team");
        db.update(data => {
            const p = data.players.find(x => x.id === pid);
            const t = data.teams.find(x => x.id === tid);
            p.transferHistory = p.transferHistory || []; p.transferHistory.push(`Loaned to ${t.name}`);
            p.loanStatus = { originalTeamId: p.teamId, legsRemaining: 2 }; p.teamId = tid;
            return data;
        });
        util.notify("Loan Started (2 Legs)"); window.modals.openTransferMarket();
    },
    renameSeason: () => {
        const name = document.getElementById('seasonNameInp').value;
        if(name) { db.update(data => { data.seasonName = name; return data; }); util.notify("Season Renamed"); }
    },
    resetSeason: () => {
        if(confirm("DANGER: RESET SEASON? Matches will be deleted.")) {
            db.update(data => { data.matches = []; data.players.forEach(p => { p.hype=0; p.transferCount=0; p.loanStatus=null; p.transferHistory=[]; }); return data; });
            util.notify("Season Reset"); window.app.nav('registry'); document.getElementById('modal-overlay').classList.add('hidden');
        }
    }
};

window.modals = {
    openSeasonControl: () => {
        const data = db.get();
        const b = document.getElementById('modal-body');
        b.innerHTML = `<h2 class="neon-text">Season Control</h2><div style="margin:20px 0;"><label>Season Name</label><div class="flex"><input type="text" id="seasonNameInp" value="${data.seasonName}"><button class="btn btn-primary" onclick="actions.renameSeason()">Save</button></div></div><div style="border-top:1px solid #333; padding-top:20px;"><button class="btn btn-danger" style="width:100%;" onclick="actions.resetSeason()">⚠️ RESTART SEASON</button></div><button class="btn" style="margin-top:20px;" onclick="document.getElementById('modal-overlay').classList.add('hidden')">Close</button>`;
        document.getElementById('modal-overlay').classList.remove('hidden');
    },
    openTransferMarket: () => {
        const data = db.get();
        const b = document.getElementById('modal-body');
        b.innerHTML = `<h2 class="neon-text">Transfer Market</h2><div class="grid" style="grid-template-columns: 1fr 1fr; gap:20px; margin-top:20px;"><div class="card"><h3>TRANSFER</h3><select id="tf-player"><option value="">Select Player</option>${data.players.map(p=>`<option value="${p.id}">${p.name} (${data.teams.find(t=>t.id===p.teamId).name})</option>`).join('')}</select><select id="tf-newteam"><option value="">To Team</option>${data.teams.map(t=>`<option value="${t.id}">${t.name}</option>`).join('')}</select><button class="btn btn-primary" style="width:100%; margin-top:10px;" onclick="actions.transferPlayer()">Confirm</button></div><div class="card"><h3>LOAN (2 LEGS)</h3><select id="ln-player"><option value="">Select Player</option>${data.players.filter(p=>!p.loanStatus).map(p=>`<option value="${p.id}">${p.name} (${data.teams.find(t=>t.id===p.teamId).name})</option>`).join('')}</select><select id="ln-newteam"><option value="">To Team</option>${data.teams.map(t=>`<option value="${t.id}">${t.name}</option>`).join('')}</select><button class="btn btn-warning" style="width:100%; margin-top:10px;" onclick="actions.loanPlayer()">Confirm</button></div></div><button class="btn" style="margin-top:20px;" onclick="document.getElementById('modal-overlay').classList.add('hidden')">Close</button>`;
        document.getElementById('modal-overlay').classList.remove('hidden');
    },
    openMatchCreation: () => {
        const data = db.get();
        if(data.teams.length < 2) return alert("Need 2 teams.");
        const b = document.getElementById('modal-body');
        b.innerHTML = `<h2 class="neon-text">Record Match</h2><div class="grid" style="grid-template-columns: 1fr 1fr; gap:20px; margin-bottom:20px;"><div><label>Team A</label><select id="m-teamA" onchange="window.modals.renderMatchPlayers()"><option value="">Select Team</option>${data.teams.map(t=>`<option value="${t.id}">${t.name}</option>`).join('')}</select></div><div><label>Team B</label><select id="m-teamB" onchange="window.modals.renderMatchPlayers()"><option value="">Select Team</option>${data.teams.map(t=>`<option value="${t.id}">${t.name}</option>`).join('')}</select></div></div><div style="background:rgba(0,0,0,0.3); padding:10px; margin-bottom:20px;"><h4>Leg 1</h4><div class="flex"><input type="number" id="m-l1-a" placeholder="A"><input type="number" id="m-l1-b" placeholder="B"></div><h4>Leg 2</h4><div class="flex"><input type="number" id="m-l2-a" placeholder="A"><input type="number" id="m-l2-b" placeholder="B"></div></div><div id="m-player-stats-area"></div><div style="margin-top:20px; text-align:right;"><button class="btn btn-danger" onclick="document.getElementById('modal-overlay').classList.add('hidden')">Cancel</button> <button class="btn btn-primary" onclick="window.modals.saveMatch()">SAVE</button></div>`;
        document.getElementById('modal-overlay').classList.remove('hidden');
    },
    renderMatchPlayers: () => {
        const tA = document.getElementById('m-teamA').value;
        const tB = document.getElementById('m-teamB').value;
        if(!tA || !tB || tA===tB) { document.getElementById('m-player-stats-area').innerHTML=''; return; }
        const data = db.get();
        const allP = [...data.players.filter(p=>p.teamId===tA), ...data.players.filter(p=>p.teamId===tB)];
        let html = `<h4>Player Stats</h4><div style="max-height:300px; overflow-y:scroll; border:1px solid #333; padding:10px;">`;
        allP.forEach(p => {
            const col = data.teams.find(t=>t.id===p.teamId).color;
            html += `<div style="border-bottom:1px solid #333; padding:10px 0;"><div style="display:flex; justify-content:space-between; align-items:center;"><span style="font-weight:bold; color:${col}">${p.name}</span><div class="chk-container"><label><input type="checkbox" class="leg-check" data-pid="${p.id}" data-leg="1" checked> L1</label><label><input type="checkbox" class="leg-check" data-pid="${p.id}" data-leg="2" checked> L2</label></div></div><div class="grid" style="grid-template-columns:repeat(4,1fr); gap:5px; margin-top:5px;"><input type="number" placeholder="G" class="stat-inp" data-pid="${p.id}" data-type="goals"><input type="number" placeholder="A" class="stat-inp" data-pid="${p.id}" data-type="assists"><input type="number" placeholder="Sv" class="stat-inp" data-pid="${p.id}" data-type="saves"><input type="number" placeholder="Tk" class="stat-inp" data-pid="${p.id}" data-type="tackles"></div></div>`;
        });
        html += `</div><div class="grid" style="grid-template-columns:1fr 1fr; margin-top:10px;"><div><label>MVP</label><select id="m-mvp"><option value="">Select MVP</option>${allP.map(p=>`<option value="${p.id}">${p.name}</option>`).join('')}</select></div><div><label>MOTM</label><select id="m-motm"><option value="">Select MOTM</option>${allP.map(p=>`<option value="${p.id}">${p.name}</option>`).join('')}</select></div></div>`;
        document.getElementById('m-player-stats-area').innerHTML = html;
    },
    saveMatch: () => {
        const tA=document.getElementById('m-teamA').value, tB=document.getElementById('m-teamB').value;
        const mvp=document.getElementById('m-mvp').value, motm=document.getElementById('m-motm').value;
        if(!mvp || !motm) return alert("Select MVP/MOTM");
        const data = db.get();
        const pStats = [];
        const getObj = (pid) => {
            let o = pStats.find(x=>x.playerId===pid);
            if(!o) { o={playerId:pid, teamId: data.players.find(p=>p.id===pid).teamId, goals:0, assists:0, saves:0, tackles:0, playedLeg1:false, playedLeg2:false}; pStats.push(o); }
            return o;
        };
        document.querySelectorAll('.stat-inp').forEach(i => { getObj(i.dataset.pid)[i.dataset.type] = i.value||0; });
        document.querySelectorAll('.leg-check').forEach(c => { if(c.checked) { if(c.dataset.leg==="1") getObj(c.dataset.pid).playedLeg1=true; else getObj(c.dataset.pid).playedLeg2=true; } });

        db.update(d => {
            d.matches.push({ id:util.uuid(), teamAId:tA, teamBId:tB, leg1ScoreA:document.getElementById('m-l1-a').value||0, leg1ScoreB:document.getElementById('m-l1-b').value||0, leg2ScoreA:document.getElementById('m-l2-a').value||0, leg2ScoreB:document.getElementById('m-l2-b').value||0, mvpId:mvp, motmId:motm, playerStats:pStats, timestamp:Date.now() });
            pStats.forEach(ps => {
                const p = d.players.find(x=>x.id===ps.playerId);
                if(p && p.loanStatus) {
                    let used = (ps.playedLeg1?1:0) + (ps.playedLeg2?1:0);
                    p.loanStatus.legsRemaining -= used;
                    if(p.loanStatus.legsRemaining <= 0) { p.teamId = p.loanStatus.originalTeamId; p.loanStatus = null; p.transferHistory.push("Loan Ended"); util.notify(p.name + " returned from loan"); }
                }
            });
            return d;
        });
        document.getElementById('modal-overlay').classList.add('hidden'); util.notify("Match Saved");
    }
};

window.app.init();
</script>
</body>
</html>
