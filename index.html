<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Video Match - Connect</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-database.js"></script>
    <script src="https://unpkg.com/peerjs@1.4.7/dist/peerjs.min.js"></script>
    <style>
        /* লেআউট এবং ভিডিও ফিক্স */
        #remoteVideo { 
            object-fit: cover; 
            background: #000; /* কানেক্ট হওয়ার আগে স্ক্রিন কালো রাখবে */
            z-index: 10; 
        }

        /* প্লেয়ার আইকন এবং কন্ট্রোলস হাইড করা */
        video::-webkit-media-controls { display:none !important; }
        video::-webkit-media-controls-start-playback-button { display: none !important; }
        
        #localVideo { 
            object-fit: cover; 
            background: #333; 
            border: 2px solid rgba(255,255,255,0.3);
            border-radius: 15px; 
            z-index: 100;
            box-shadow: 0 10px 20px rgba(0,0,0,0.5);
        }

        .controls-layer {
            position: absolute;
            bottom: 50px;
            left: 0;
            right: 0;
            z-index: 200;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 20px;
        }

        .mirror { transform: scaleX(-1); }
        
        #chatBox {
            max-width: 85%;
            background: rgba(0, 0, 0, 0.7);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            border: 1px solid rgba(255,255,255,0.1);
        }
    </style>
</head>
<body class="bg-black text-white font-sans overflow-hidden">

    <div id="landingPage" class="fixed inset-0 z-[500] flex flex-col items-center justify-center bg-gradient-to-br from-indigo-900 via-purple-900 to-pink-800 p-6 text-center">
        <div class="mb-6 bg-white/10 p-5 rounded-full backdrop-blur-md">
            <svg class="w-16 h-16 text-pink-400" fill="currentColor" viewBox="0 0 24 24"><path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/></svg>
        </div>
        <h1 class="text-4xl font-extrabold mb-2 tracking-tight">Video Match</h1>
        <p class="text-sm opacity-80 mb-10 max-w-xs leading-relaxed">Meet With New People and Make Some Friends❤️ Click On Start Matching!</p>
        <button onclick="entryApp()" class="bg-white text-indigo-900 font-bold py-4 px-12 rounded-full shadow-2xl transition transform active:scale-95 text-lg">
            Start Matching
        </button>
        
        
<button onclick="https://www.google.com" 
class="mt-10 bg-pink-500 text-white font-bold py-4 px-12 rounded-full shadow-2xl transition transform active:scale-95 text-lg">
    Download App
</button>
        
        
    </div>

    <div id="appContainer" class="hidden relative h-screen w-full bg-black">
        
        <video id="remoteVideo" autoplay playsinline webkit-playsinline class="absolute inset-0 w-full h-full bg-black"></video>
        
        <video id="localVideo" autoplay muted playsinline class="absolute top-6 right-4 w-28 h-40 mirror"></video>

        <div class="controls-layer">
            
            <div id="status" class="bg-black/50 backdrop-blur-sm px-4 py-1 rounded-full text-xs font-semibold border border-white/20">
                Searching...
            </div>

            <div id="chatBox" class="hidden w-80 p-4 mb-2">
                <div id="messages" class="h-24 overflow-y-auto text-xs space-y-2 mb-3 scrollbar-hide"></div>
                <div class="flex gap-2">
                    <input id="msgInput" type="text" placeholder="Type Messages..." class="flex-1 bg-white/10 p-2 rounded-full text-xs outline-none border border-white/20 text-white">
                    <button onclick="sendMsg()" class="bg-pink-500 p-2 px-4 rounded-full text-xs font-bold">Send</button>
                </div>
            </div>

            <div class="flex items-center gap-6">
                <button onclick="stopMatch()" class="bg-red-600/90 p-4 rounded-full shadow-lg active:scale-90 transition">
                    <svg class="w-6 h-6" fill="white" viewBox="0 0 24 24"><path d="M12 2c5.52 0 10 4.48 10 10s-4.48 10-10 10S2 17.52 2 12 6.48 2 12 2zM10 10h4v4h-4z"/></svg>
                </button>

                <button id="skipBtn" onclick="skipMatch()" class="bg-white text-black font-extrabold px-12 py-4 rounded-full shadow-2xl active:scale-95 transition flex items-center gap-3">
                    NEXT
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-width="3" d="M13 5l7 7-7 7M5 5l7 7-7 7"></path></svg>
                </button>

                <button onclick="toggleChat()" class="bg-indigo-600/90 p-4 rounded-full shadow-lg active:scale-90 transition">
                    <svg class="w-6 h-6" fill="white" viewBox="0 0 24 24"><path d="M20 2H4c-1.1 0-2 .9-2 2v18l4-4h14c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2z"/></svg>
                </button>
            </div>
        </div>
    </div>

    <script>
        const firebaseConfig = {
  apiKey: "AIzaSyDvMIYdkDIybQOag5z-Ci9EwMY425mPlwk",
  authDomain: "test-67af4.firebaseapp.com",
  databaseURL: "https://test-67af4-default-rtdb.firebaseio.com",
  projectId: "test-67af4",
  storageBucket: "test-67af4.firebasestorage.app",
  messagingSenderId: "696051017684",
  appId: "1:696051017684:web:72e8327e6a72a256655841",
  measurementId: "G-D28T7SXQX1"
};
        firebase.initializeApp(firebaseConfig);
        const db = firebase.database();

        let userId = localStorage.getItem('guestId') || "user_" + Math.floor(Math.random() * 1000000);
        localStorage.setItem('guestId', userId);

        let localStream, peer, currentCall, dataConn;

        function entryApp() {
            document.getElementById('landingPage').style.display = 'none';
            document.getElementById('appContainer').classList.remove('hidden');
            initPeer();
        }

        function initPeer() {
            peer = new Peer(userId);
            
            navigator.mediaDevices.getUserMedia({ video: true, audio: true }).then(stream => {
                localStream = stream;
                document.getElementById('localVideo').srcObject = stream;
                startMatch();
            }).catch(err => {
                alert("Need Camera and Mic Permission।");
                location.reload();
            });

            peer.on('call', call => {
                call.answer(localStream);
                handleCall(call);
            });

            peer.on('connection', conn => {
                dataConn = conn;
                setupDataHandler();
            });
        }

        function handleCall(call) {
            currentCall = call;
            call.on('stream', remoteStream => {
                const rv = document.getElementById('remoteVideo');
                rv.srcObject = remoteStream;
                
                // অটোপ্লে ব্লক এড়ানোর জন্য লজিক
                rv.onloadedmetadata = () => {
                    rv.play().catch(e => {
                        console.log("Autoplay blocked, waiting for interaction");
                        // স্ক্রিনে ক্লিক করলে ভিডিও চালু হবে
                        document.body.addEventListener('click', () => rv.play(), {once: true});
                    });
                };
                
                document.getElementById('status').innerText = "Connected! 🟢";
            });
        }

        function startMatch() {
            document.getElementById('status').innerText = "Searching for someone...";
            const waitingRef = db.ref('waiting_room');
            
            waitingRef.once('value', snapshot => {
                let foundPeer = null;
                snapshot.forEach(child => {
                    if (child.key !== userId) foundPeer = child.key;
                });

                if (foundPeer) {
                    db.ref('waiting_room/' + foundPeer).remove();
                    const call = peer.call(foundPeer, localStream);
                    dataConn = peer.connect(foundPeer);
                    setupDataHandler();
                    handleCall(call);
                } else {
                    waitingRef.child(userId).set(true);
                    waitingRef.child(userId).onDisconnect().remove();
                }
            });
        }

        function skipMatch() {
            if (currentCall) currentCall.close();
            if (dataConn) dataConn.close();
            document.getElementById('remoteVideo').srcObject = null;
            document.getElementById('messages').innerHTML = "";
            startMatch();
        }

        function stopMatch() {
            location.reload(); 
        }

        function toggleChat() {
            const chat = document.getElementById('chatBox');
            chat.classList.toggle('hidden');
        }

        function setupDataHandler() {
            dataConn.on('data', data => {
                const msgDiv = document.createElement('div');
                msgDiv.innerHTML = `<span class="text-pink-400 font-bold">Stranger:</span> <span class="text-white">${data}</span>`;
                document.getElementById('messages').appendChild(msgDiv);
                document.getElementById('messages').scrollTop = document.getElementById('messages').scrollHeight;
            });
        }

        function sendMsg() {
            const val = document.getElementById('msgInput').value;
            if (val && dataConn) {
                dataConn.send(val);
                const msgDiv = document.createElement('div');
                msgDiv.innerHTML = `<span class="text-indigo-400 font-bold">You:</span> <span class="text-white">${val}</span>`;
                document.getElementById('messages').appendChild(msgDiv);
                document.getElementById('messages').scrollTop = document.getElementById('messages').scrollHeight;
                document.getElementById('msgInput').value = "";
            }
        }
    </script>
</body>
</html>
