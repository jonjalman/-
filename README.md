<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>바카라 게임</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-slate-950 text-white min-h-screen flex items-center justify-center">

    <div id="game-container" class="w-full max-w-sm p-6 bg-slate-900 rounded-2xl shadow-2xl border border-slate-700">
        <h1 class="text-2xl font-bold text-center mb-6">럭셔리 바카라</h1>
        
        <div id="login-section">
            <button id="guestLoginBtn" class="w-full bg-indigo-600 hover:bg-indigo-700 text-white py-4 rounded-xl font-bold transition">게스트로 입장하기</button>
        </div>

        <div id="game-section" class="hidden">
            <div class="text-center mb-6">
                <p class="text-sm text-slate-400">보유 자산</p>
                <h2 id="balanceText" class="text-3xl font-mono font-bold text-emerald-400">₩10,000,000</h2>
            </div>
            <div class="grid grid-cols-2 gap-3">
                <button onclick="placeBet('player', 10000)" class="bg-rose-600 py-3 rounded-lg font-bold">Player</button>
                <button onclick="placeBet('banker', 10000)" class="bg-blue-600 py-3 rounded-lg font-bold">Banker</button>
            </div>
        </div>
    </div>

    <script>
        let balance = 10000000;
        let gamePhase = "WAITING_FOR_BETS";

        document.getElementById('guestLoginBtn').addEventListener('click', () => {
            document.getElementById('login-section').classList.add('hidden');
            document.getElementById('game-section').classList.remove('hidden');
            gamePhase = "WAITING_FOR_BETS";
        });

        function placeBet(type, amount) {
            if (gamePhase !== "WAITING_FOR_BETS") return alert("베팅 시간이 아닙니다.");
            if (balance < amount) return alert("잔액이 부족합니다.");
            
            balance -= amount;
            document.getElementById('balanceText').innerText = `₩${balance.toLocaleString()}`;
            alert(`${type}에 ${amount.toLocaleString()}원 베팅!`);
        }
    </script>
</body>
</html>
