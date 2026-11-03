# linuxvw44-jpg.github.io
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>Eggs on the rock</title>
  <style>
    * { box-sizing: border-box; }

    body {
      font-family: 'Pretendard', 'Segoe UI', Tahoma, sans-serif;
      background: radial-gradient(circle at center, #131324 0%, #07070c 100%);
      color: #cdd6f4;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 20px;
      margin: 0;
      user-select: none;
      overflow-x: hidden;
      min-height: 100vh;
    }

    h1 {
      color: #f9e2af;
      margin-top: 5px;
      margin-bottom: 15px;
      text-shadow: 0 0 20px rgba(249, 226, 175, 0.6), 0 0 40px rgba(203, 166, 247, 0.3);
      font-size: 28px;
      letter-spacing: 1px;
    }

    /* 상단 대시보드 */
    .stats-container {
      background: rgba(24, 24, 37, 0.75);
      backdrop-filter: blur(12px);
      border: 1px solid rgba(203, 166, 247, 0.25);
      padding: 14px 25px;
      border-radius: 18px;
      display: flex;
      gap: 22px;
      margin-bottom: 20px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.7), inset 0 1px 1px rgba(255,255,255,0.08);
      align-items: center;
      flex-wrap: wrap;
      justify-content: center;
    }

    .stat-item {
      font-size: 15px;
      font-weight: bold;
      letter-spacing: 0.5px;
    }

    .stat-val { color: #f9e2af; text-shadow: 0 0 8px rgba(249,226,175,0.4); }

    .collection-open-btn {
      background: linear-gradient(135deg, #cba6f7 0%, #b4befe 100%);
      color: #11111b;
      border: none;
      padding: 9px 18px;
      font-size: 14px;
      font-weight: bold;
      border-radius: 10px;
      cursor: pointer;
      transition: 0.25s;
      box-shadow: 0 4px 15px rgba(203, 166, 247, 0.4);
    }

    .collection-open-btn:hover {
      background: linear-gradient(135deg, #f5c2e7 0%, #cba6f7 100%);
      transform: translateY(-2px);
      box-shadow: 0 6px 20px rgba(203, 166, 247, 0.6);
    }

    /* 알 선택 탭 */
    .egg-tabs {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 10px;
      margin-bottom: 20px;
      width: 100%;
      max-width: 560px;
    }

    .tab-btn {
      background: rgba(30, 30, 46, 0.7);
      backdrop-filter: blur(8px);
      color: #a6adc8;
      border: 1px solid rgba(255, 255, 255, 0.08);
      padding: 11px 6px;
      font-size: 13px;
      font-weight: bold;
      border-radius: 12px;
      cursor: pointer;
      transition: all 0.25s;
      text-align: center;
      box-shadow: 0 4px 12px rgba(0,0,0,0.3);
    }

    .tab-btn:hover:not(:disabled) {
      background: rgba(49, 50, 68, 0.9);
      color: #cdd6f4;
      border-color: rgba(137, 180, 250, 0.4);
    }

    .tab-btn.active {
      background: linear-gradient(135deg, #89b4fa 0%, #74c7ec 100%);
      color: #11111b;
      border-color: #89b4fa;
      box-shadow: 0 0 20px rgba(137, 180, 250, 0.5);
    }

    .tab-btn:disabled {
      opacity: 0.35;
      cursor: not-allowed;
    }

    /* 메인 알 부화 영역 */
    .egg-display-panel {
      backdrop-filter: blur(16px);
      border-radius: 26px;
      padding: 25px 20px;
      width: 100%;
      max-width: 560px;
      text-align: center;
      box-shadow: 0 15px 40px rgba(0,0,0,0.7), inset 0 1px 2px rgba(255,255,255,0.15);
      display: flex;
      flex-direction: column;
      align-items: center;
      position: relative;
      overflow: hidden;
      transition: background 0.5s ease, border-color 0.5s ease, box-shadow 0.5s ease;
    }

    .panel-egg1 { background: radial-gradient(circle at center, rgba(62,56,30,0.85) 0%, rgba(20,20,30,0.9) 100%); border: 2px solid rgba(250,204,21,0.4); }
    .panel-egg2 { background: radial-gradient(circle at center, rgba(20,60,35,0.85) 0%, rgba(15,25,20,0.9) 100%); border: 2px solid rgba(74,222,128,0.4); }
    .panel-egg3 { background: radial-gradient(circle at center, rgba(15,45,75,0.85) 0%, rgba(10,18,30,0.9) 100%); border: 2px solid rgba(56,189,248,0.4); }
    .panel-egg4 { background: radial-gradient(circle at center, rgba(30,60,85,0.85) 0%, rgba(12,20,35,0.9) 100%); border: 2px solid rgba(147,197,253,0.4); }
    .panel-egg5 { background: radial-gradient(circle at center, rgba(85,25,25,0.85) 0%, rgba(25,12,12,0.9) 100%); border: 2px solid rgba(248,113,113,0.5); }
    .panel-egg6 { background: radial-gradient(circle at center, rgba(55,25,85,0.85) 0%, rgba(18,10,30,0.9) 100%); border: 2px solid rgba(192,132,252,0.5); box-shadow: 0 0 35px rgba(139,92,246,0.3); }

    .egg-title {
      font-size: 23px;
      color: #f9e2af;
      margin: 0;
      text-shadow: 0 0 12px rgba(249,226,175,0.5);
      z-index: 5;
    }

    .egg-cost-info {
      font-size: 13px;
      color: #a6adc8;
      margin: 6px 0 12px 0;
      z-index: 5;
    }

    .egg-drop-preview {
      width: 100%;
      background: rgba(17, 17, 27, 0.85);
      border: 1px solid rgba(49, 50, 68, 0.8);
      border-radius: 14px;
      padding: 12px 14px;
      margin-bottom: 15px;
      text-align: left;
      z-index: 5;
    }

    .egg-drop-preview-title {
      font-size: 11px;
      color: #cba6f7;
      font-weight: bold;
      margin-bottom: 8px;
      display: flex;
      align-items: center;
      gap: 4px;
      letter-spacing: 0.5px;
    }

    .drop-list-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 5px 12px;
      max-height: 110px;
      overflow-y: auto;
      padding-right: 4px;
    }

    .drop-item-row {
      display: flex;
      justify-content: space-between;
      font-size: 10px;
      padding: 3px 6px;
      border-radius: 6px;
      background: rgba(24, 24, 37, 0.9);
    }

    .drop-item-name {
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
      max-width: 120px;
    }

    .huge-egg-container {
      width: 180px;
      height: 180px;
      margin: 5px 0 15px 0;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
      position: relative;
      animation: floatEgg 3.5s ease-in-out infinite;
      transition: transform 0.2s;
      z-index: 5;
    }
    .huge-egg-container:hover { transform: scale(1.06); }

    @keyframes floatEgg {
      0%, 100% { transform: translateY(0) rotate(0deg); }
      50% { transform: translateY(-10px) rotate(1.5deg); }
    }

    .huge-egg-container svg {
      width: 100%;
      height: 100%;
      position: relative;
      z-index: 2;
    }

    .egg-effect-ring {
      position: absolute;
      width: 140px;
      height: 140px;
      border-radius: 50%;
      z-index: 1;
      pointer-events: none;
    }

    .effect-egg1 { background: radial-gradient(circle, rgba(249,226,175,0.4) 0%, transparent 70%); box-shadow: 0 0 30px rgba(249,226,175,0.5); animation: pulseGlow 2.5s ease-in-out infinite alternate; }
    .effect-egg2 { background: radial-gradient(circle, rgba(166,227,161,0.4) 0%, transparent 70%); box-shadow: 0 0 35px rgba(166,227,161,0.6); animation: pulseGlow 2s ease-in-out infinite alternate; }
    .effect-egg3 { background: radial-gradient(circle, rgba(137,180,250,0.45) 0%, transparent 70%); box-shadow: 0 0 35px rgba(137,180,250,0.6); animation: pulseGlow 2.5s ease-in-out infinite alternate; }
    .effect-egg4 { background: radial-gradient(circle, rgba(180,190,254,0.45) 0%, transparent 70%); box-shadow: 0 0 40px rgba(56,189,248,0.65); animation: auroraPulse 3s ease-in-out infinite alternate; }
    .effect-egg5 { background: radial-gradient(circle, rgba(243,139,168,0.5) 0%, transparent 70%); box-shadow: 0 0 45px rgba(249,115,22,0.7); animation: magmaBurn 1.8s ease-in-out infinite alternate; }
    .effect-egg6 { background: radial-gradient(circle, rgba(203,166,247,0.5) 0%, transparent 70%); box-shadow: 0 0 50px rgba(139,92,246,0.8); animation: cosmosWarp 3.5s ease-in-out infinite alternate; }

    @keyframes pulseGlow { 0% { transform: scale(0.9); opacity: 0.6; } 100% { transform: scale(1.15); opacity: 1; } }
    @keyframes auroraPulse { 0% { transform: scale(0.92) rotate(0deg); filter: hue-rotate(0deg); } 100% { transform: scale(1.18) rotate(180deg); filter: hue-rotate(45deg); } }
    @keyframes magmaBurn { 0% { transform: scale(0.95); opacity: 0.7; box-shadow: 0 0 30px rgba(239,68,68,0.6); } 100% { transform: scale(1.15); opacity: 1; box-shadow: 0 0 55px rgba(245,158,11,0.9); } }
    @keyframes cosmosWarp { 0% { transform: scale(0.9) rotate(0deg); } 50% { transform: scale(1.2) rotate(180deg); } 100% { transform: scale(0.9) rotate(360deg); } }

    .theme-fx-layer {
      position: absolute;
      top: 0; left: 0; width: 100%; height: 100%;
      pointer-events: none;
      z-index: 3;
      overflow: hidden;
    }

    .fx-leaf {
      position: absolute;
      background: #a6e3a1;
      opacity: 0.7;
      border-radius: 60% 0 60% 0;
      animation: leafFly 4s linear infinite;
    }
    @keyframes leafFly {
      0% { transform: translate(-20px, 180px) rotate(0deg); opacity: 0; }
      20% { opacity: 0.8; }
      80% { opacity: 0.8; }
      100% { transform: translate(320px, -20px) rotate(360deg); opacity: 0; }
    }

    .fx-coral {
      position: absolute;
      bottom: 0;
      width: 100%;
      height: 45px;
      background: radial-gradient(ellipse at bottom, rgba(137,180,250,0.25) 0%, transparent 80%);
      display: flex;
      justify-content: space-around;
      align-items: flex-end;
      padding-bottom: 5px;
    }
    .coral-item {
      font-size: 22px;
      animation: coralSway 2.5s ease-in-out infinite alternate;
      transform-origin: bottom center;
    }
    .coral-item:nth-child(2) { animation-delay: 0.5s; animation-duration: 3s; }
    .coral-item:nth-child(3) { animation-delay: 1s; animation-duration: 2.2s; }
    @keyframes coralSway {
      0% { transform: rotate(-8deg); }
      100% { transform: rotate(12deg); }
    }

    .fx-snowflake {
      position: absolute;
      background: #ffffff;
      border-radius: 50%;
      animation: snowFall linear infinite;
    }
    @keyframes snowFall {
      0% { transform: translateY(-10px) translateX(0); opacity: 0; }
      20% { opacity: 0.9; }
      100% { transform: translateY(320px) translateX(30px); opacity: 0.1; }
    }

    .fx-lava-bubble {
      position: absolute;
      bottom: 0;
      background: radial-gradient(circle, #facc15 0%, #f43f5e 60%, transparent 100%);
      border-radius: 50%;
      animation: lavaUp ease-in infinite;
    }
    @keyframes lavaUp {
      0% { transform: translateY(20px) scale(0.4); opacity: 0; }
      30% { opacity: 1; }
      100% { transform: translateY(-180px) scale(1.4); opacity: 0; }
    }

    .fx-star {
      position: absolute;
      background: #ffffff;
      border-radius: 50%;
      box-shadow: 0 0 8px #f9e2af, 0 0 15px #cba6f7;
      animation: starTwinkle ease-in-out infinite alternate;
    }
    @keyframes starTwinkle {
      0% { transform: scale(0.4); opacity: 0.2; }
      100% { transform: scale(1.3); opacity: 1; }
    }

    .hatch-btn-group {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 8px;
      width: 100%;
      margin-top: 10px;
      z-index: 5;
    }

    button {
      background: linear-gradient(135deg, #89b4fa 0%, #b4befe 100%);
      color: #11111b;
      border: none;
      padding: 11px 5px;
      font-size: 13px;
      font-weight: bold;
      border-radius: 10px;
      cursor: pointer;
      transition: 0.2s;
      box-shadow: 0 4px 12px rgba(137, 180, 250, 0.3);
    }

    button:hover:not(:disabled) {
      background: linear-gradient(135deg, #b4befe 0%, #cba6f7 100%);
      transform: translateY(-2px);
      box-shadow: 0 6px 16px rgba(180, 190, 254, 0.5);
    }

    button:disabled {
      background: #313244;
      color: #585b70;
      cursor: not-allowed;
      transform: none;
      box-shadow: none;
    }

    .auto-btn {
      background: linear-gradient(135deg, #fab387 0%, #f9e2af 100%) !important;
      color: #11111b !important;
      width: 100%;
      max-width: 560px;
      padding: 13px;
      font-size: 14px;
      border-radius: 12px;
      font-weight: bold;
      margin-top: 12px;
      box-shadow: 0 6px 18px rgba(250, 179, 135, 0.3) !important;
    }
    .auto-btn:hover { background: linear-gradient(135deg, #f9e2af 0%, #fab387 100%) !important; }
    .auto-btn.active {
      background: linear-gradient(135deg, #f38ba8 0%, #eba0ac 100%) !important;
      color: #11111b !important;
      box-shadow: 0 0 25px rgba(243, 139, 168, 0.6) !important;
      animation: pulseAuto 1s infinite alternate;
    }

    @keyframes pulseAuto {
      0% { transform: scale(1); }
      100% { transform: scale(1.02); }
    }

    .boss-btn {
      background: linear-gradient(135deg, #eba0ac 0%, #f38ba8 100%) !important;
      color: #11111b !important;
      width: 100%;
      max-width: 560px;
      padding: 13px;
      font-size: 14px;
      border-radius: 12px;
      font-weight: bold;
      margin-top: 8px;
      box-shadow: 0 6px 18px rgba(235, 160, 172, 0.3) !important;
    }
    .boss-btn:hover:not(:disabled) { background: linear-gradient(135deg, #f38ba8 0%, #eba0ac 100%) !important; }

    .test-cheat-btn {
      background: rgba(249, 226, 175, 0.15) !important;
      color: #f9e2af !important;
      width: 100%;
      max-width: 560px;
      padding: 10px;
      font-size: 13px;
      border-radius: 12px;
      font-weight: bold;
      margin-top: 8px;
      border: 1px dashed #f9e2af;
      box-shadow: none !important;
    }
    .test-cheat-btn:hover { background: rgba(249, 226, 175, 0.25) !important; transform: none !important; }

    .reincarnate-btn {
      background: linear-gradient(135deg, #f38ba8 0%, #eba0ac 100%) !important;
      color: #11111b !important;
      width: 100%;
      max-width: 560px;
      padding: 14px;
      font-size: 15px;
      border-radius: 14px;
      font-weight: bold;
      margin-top: 8px;
      box-shadow: 0 6px 20px rgba(243, 139, 168, 0.35) !important;
    }
    .reincarnate-btn:hover { background: linear-gradient(135deg, #eba0ac 0%, #f38ba8 100%) !important; }

    .log-box {
      width: 100%;
      max-width: 560px;
      height: 85px;
      background: rgba(17, 17, 27, 0.85);
      backdrop-filter: blur(8px);
      border: 1px solid rgba(49, 50, 68, 0.8);
      border-radius: 14px;
      padding: 10px;
      overflow-y: auto;
      font-size: 12px;
      line-height: 1.5;
      margin-top: 15px;
      box-shadow: inset 0 2px 6px rgba(0,0,0,0.5);
    }

    .collection-modal-overlay {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(7, 7, 12, 0.85);
      backdrop-filter: blur(10px);
      display: flex;
      justify-content: center;
      align-items: center;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s ease;
      z-index: 1500;
    }

    .collection-modal-overlay.active { opacity: 1; pointer-events: auto; }

    .collection-modal-content {
      background: rgba(24, 24, 37, 0.95);
      border: 2px solid rgba(203, 166, 247, 0.5);
      border-radius: 24px;
      padding: 22px;
      max-width: 740px;
      width: 92%;
      max-height: 82vh;
      display: flex;
      flex-direction: column;
      box-shadow: 0 0 50px rgba(203, 166, 247, 0.25);
    }

    .collection-modal-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 2px solid rgba(49, 50, 68, 0.8);
      padding-bottom: 12px;
      margin-bottom: 15px;
    }

    .collection-modal-header h2 {
      margin: 0;
      color: #cba6f7;
      font-size: 18px;
      text-shadow: 0 0 10px rgba(203,166,247,0.4);
    }

    .collection-list {
      list-style: none;
      padding: 0;
      margin: 0;
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
      gap: 12px;
      overflow-y: auto;
      padding-right: 5px;
    }

    .collection-item {
      background: rgba(17, 17, 27, 0.9);
      border: 1px solid rgba(49, 50, 68, 0.8);
      border-radius: 14px;
      padding: 10px;
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      font-size: 11px;
      position: relative;
      transition: transform 0.2s;
    }
    .collection-item:hover:not(.locked) { transform: translateY(-3px); }

    .collection-item .count-badge {
      position: absolute;
      top: 6px;
      right: 6px;
      background: rgba(49, 50, 68, 0.9);
      color: #a6adc8;
      border-radius: 8px;
      padding: 2px 6px;
      font-size: 9px;
      font-weight: bold;
      border: 1px solid rgba(255,255,255,0.05);
    }

    .collection-item svg { width: 58px; height: 58px; margin: 4px 0; filter: drop-shadow(0 0 10px currentColor); }

    .rarity-Common { color: #a6adc8; }
    .rarity-Uncommon { color: #a6e3a1; }
    .rarity-Rare { color: #89b4fa; }
    .rarity-Epic { color: #cba6f7; }
    .rarity-Legendary { color: #fab387; }
    .rarity-Mythical { color: #f38ba8; text-shadow: 0 0 8px #f38ba8, 0 0 16px #ff7675; }
    .rarity-Exotic { animation: rainbowTextGlow 3s infinite alternate; }

    @keyframes rainbowTextGlow {
      0% { color: #ff7675; text-shadow: 0 0 8px #ff7675, 0 0 16px #fab387; filter: drop-shadow(0 0 8px #ff7675); }
      33% { color: #a6e3a1; text-shadow: 0 0 8px #a6e3a1, 0 0 16px #89b4fa; filter: drop-shadow(0 0 8px #a6e3a1); }
      66% { color: #cba6f7; text-shadow: 0 0 8px #cba6f7, 0 0 16px #f5c2e7; filter: drop-shadow(0 0 8px #cba6f7); }
      100% { color: #f9e2af; text-shadow: 0 0 8px #f9e2af, 0 0 16px #ff7675; filter: drop-shadow(0 0 8px #f9e2af); }
    }

    .collection-item.rarity-Common { border-color: rgba(69, 71, 90, 0.8); }
    .collection-item.rarity-Uncommon { border-color: rgba(166, 227, 161, 0.4); }
    .collection-item.rarity-Rare { border-color: rgba(137, 180, 250, 0.4); }
    .collection-item.rarity-Epic { border-color: rgba(203, 166, 247, 0.4); }
    .collection-item.rarity-Legendary { border-color: rgba(250, 179, 135, 0.5); box-shadow: inset 0 0 10px rgba(250, 179, 135, 0.2); }
    .collection-item.rarity-Mythical { border-color: #f38ba8; box-shadow: inset 0 0 20px rgba(243, 139, 168, 0.35), 0 0 15px rgba(243, 139, 168, 0.25); }
    .collection-item.rarity-Exotic { 
      border-color: #f38ba8; 
      animation: exoticBoxBorder 3s infinite alternate; 
    }
    @keyframes exoticBoxBorder {
      0% { box-shadow: inset 0 0 20px rgba(255, 118, 117, 0.45), 0 0 15px rgba(250, 179, 135, 0.35); border-color: #ff7675; }
      50% { box-shadow: inset 0 0 20px rgba(137, 180, 250, 0.45), 0 0 15px rgba(166, 227, 161, 0.35); border-color: #89b4fa; }
      100% { box-shadow: inset 0 0 20px rgba(203, 166, 247, 0.45), 0 0 15px rgba(245, 194, 231, 0.35); border-color: #cba6f7; }
    }

    .locked { opacity: 0.25; filter: grayscale(100%); }

    .cinematic-overlay {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(7, 7, 12, 0.95);
      backdrop-filter: blur(12px);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 2000;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s ease;
    }

    .cinematic-overlay.active { opacity: 1; pointer-events: auto; }

    .cinematic-title {
      font-size: 24px;
      color: #f9e2af;
      margin-bottom: 25px;
      text-shadow: 0 0 20px rgba(249,226,175,0.6);
      letter-spacing: 0.5px;
    }

    .cinematic-eggs-area {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 20px;
      max-width: 600px;
      padding: 15px;
    }

    .floating-egg {
      width: 90px;
      height: 90px;
      animation: superShake 0.4s infinite;
    }

    @keyframes superShake {
      0% { transform: translate(0, 0) rotate(0deg); }
      20% { transform: translate(-6px, -10px) rotate(-15deg) scale(1.1); }
      40% { transform: translate(6px, 10px) rotate(15deg) scale(1.1); }
      60% { transform: translate(-6px, 6px) rotate(-10deg) scale(1.05); }
      80% { transform: translate(6px, -6px) rotate(10deg) scale(1.05); }
      100% { transform: translate(0, 0) rotate(0deg); }
    }

    .floating-creature {
      display: flex;
      flex-direction: column;
      align-items: center;
      animation: popOut 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
      background: rgba(30, 30, 46, 0.9);
      border: 2px solid currentColor;
      padding: 12px;
      border-radius: 16px;
      width: 120px;
      box-shadow: 0 0 25px currentColor;
    }

    @keyframes popOut {
      0% { transform: scale(0) translateY(40px); opacity: 0; }
      100% { transform: scale(1) translateY(0); opacity: 1; }
    }

    .floating-creature svg { width: 60px; height: 60px; margin-bottom: 6px; }

    /* ==========================================================================
       [보스전 배경 테마 & 초고퀄리티 CANVAS 애니메이션 연출]
       ========================================================================== */
    .boss-battle-overlay {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(7, 7, 12, 0.97);
      backdrop-filter: blur(15px);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 2500;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s ease, background 0.5s ease;
      overflow: hidden;
    }
    .boss-battle-overlay.active { opacity: 1; pointer-events: auto; }

    #boss-canvas {
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      pointer-events: none;
      z-index: 1;
    }

    .earthquake-shake {
      animation: heavyEarthQuake 0.08s infinite alternate ease-in-out;
    }
    @keyframes heavyEarthQuake {
      0% { transform: translate(-5px, 3px) rotate(-0.5deg); }
      100% { transform: translate(6px, -4px) rotate(0.5deg); }
    }

    .battle-arena {
      display: flex; align-items: center; justify-content: space-around; width: 100%; max-width: 600px; margin: 25px 0;
      position: relative; z-index: 5;
    }

    .boss-fighter {
      width: 140px; height: 140px; display: flex; justify-content: center; align-items: center;
      background: radial-gradient(circle, #2a1b2e 0%, #11111b 100%); border: 3px solid #f38ba8; border-radius: 24px;
      box-shadow: 0 0 35px rgba(243,139,168,0.5); position: relative; transition: transform 0.1s;
    }
    .boss-fighter svg { width: 100px; height: 100px; }

    .boss-fighter.hit-shake { animation: bossHit 0.25s ease-in-out; }
    @keyframes bossHit {
      0% { transform: scale(1) rotate(0deg); filter: drop-shadow(0 0 25px #e74c3c); }
      25% { transform: scale(0.92) translate(-8px, 4px) rotate(-6deg); filter: brightness(1.8) drop-shadow(0 0 40px #ff7675); }
      50% { transform: scale(1.05) translate(8px, -4px) rotate(6deg); }
      75% { transform: scale(0.96) translate(-4px, -2px); }
      100% { transform: scale(1) rotate(0deg); filter: none; }
    }

    .boss-fighter.boss-dead { animation: bossExplode 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards; }
    @keyframes bossExplode {
      0% { transform: scale(1); filter: brightness(1); }
      50% { transform: scale(1.4) rotate(15deg); filter: brightness(3) drop-shadow(0 0 60px #f9e2af); }
      100% { transform: scale(0); opacity: 0; filter: brightness(5); }
    }

    .player-fighter {
      width: 110px; height: 110px; display: flex; justify-content: center; align-items: center;
      background: radial-gradient(circle, #1e2030 0%, #11111b 100%); border: 3px solid #89b4fa; border-radius: 24px;
      box-shadow: 0 0 30px rgba(137,180,250,0.5); font-size: 45px; position: relative; z-index: 5;
    }

    .player-fighter.attack-pulse { animation: playerAttack 0.3s ease; }
    @keyframes playerAttack {
      0% { transform: scale(1); }
      50% { transform: scale(1.15) translateX(12px); box-shadow: 0 0 40px #89b4fa; }
      100% { transform: scale(1); }
    }

    .attack-beam {
      position: absolute;
      top: 50%;
      left: 100px;
      width: 0px;
      height: 12px;
      background: linear-gradient(90deg, #89b4fa, #f9e2af, #f38ba8);
      border-radius: 6px;
      box-shadow: 0 0 25px #89b4fa, 0 0 15px #f38ba8;
      pointer-events: none;
      z-index: 10;
      opacity: 0;
    }
    .attack-beam.active { animation: fireBeam 0.35s ease-out forwards; }
    @keyframes fireBeam {
      0% { width: 0px; opacity: 1; transform: translateY(-50%) scaleY(1); }
      50% { width: 280px; opacity: 1; transform: translateY(-50%) scaleY(1.8); }
      100% { width: 320px; opacity: 0; transform: translateY(-50%) scaleY(0.2); }
    }

    .floating-damage {
      position: absolute;
      color: #ff7675;
      font-size: 26px;
      font-weight: 900;
      text-shadow: 0 0 10px #000, 0 0 15px #e74c3c;
      pointer-events: none;
      z-index: 20;
      animation: floatUpDamage 0.75s ease-out forwards;
      font-family: 'Arial Black', sans-serif;
    }
    @keyframes floatUpDamage {
      0% { opacity: 1; transform: translate(0, 0) scale(0.6); }
      30% { transform: translate(10px, -25px) scale(1.3); }
      100% { opacity: 0; transform: translate(25px, -65px) scale(0.9); }
    }

    .boss-timer-display {
      font-size: 20px; font-weight: bold; color: #fab387; margin-bottom: 10px;
      text-shadow: 0 0 10px rgba(250,179,135,0.4); z-index: 5;
    }
    .boss-hp-bar-container {
      width: 80%; max-width: 420px; background: rgba(49, 50, 68, 0.9); height: 22px; border-radius: 11px; overflow: hidden; border: 1px solid rgba(69, 71, 90, 0.8); margin-top: 10px; z-index: 5;
    }
    .boss-hp-bar { width: 100%; height: 100%; background: linear-gradient(90deg, #f38ba8, #eba0ac); transition: width 0.1s linear; box-shadow: 0 0 15px #f38ba8; }

    .boss-surrender-btn {
      margin-top: 25px;
      background: linear-gradient(135deg, #f38ba8 0%, #eba0ac 100%) !important;
      color: #11111b;
      font-size: 14px;
      font-weight: bold;
      padding: 10px 24px;
      border-radius: 12px;
      border: 2px solid rgba(255,255,255,0.2);
      cursor: pointer;
      box-shadow: 0 0 20px rgba(243, 139, 168, 0.5);
      transition: all 0.2s;
      z-index: 5;
    }
    .boss-surrender-btn:hover {
      background: linear-gradient(135deg, #eba0ac 0%, #f38ba8 100%) !important;
      transform: scale(1.05);
    }

    .modal-overlay {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(7, 7, 12, 0.85);
      backdrop-filter: blur(10px);
      display: flex;
      justify-content: center;
      align-items: center;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s ease;
      z-index: 1800;
    }

    .modal-overlay.active { opacity: 1; pointer-events: auto; }

    .modal-content {
      background: rgba(30, 30, 46, 0.95);
      border: 2px solid #89b4fa;
      border-radius: 22px;
      padding: 25px;
      text-align: center;
      max-width: 400px;
      width: 90%;
      box-shadow: 0 0 40px rgba(137, 180, 250, 0.35);
    }

    .modal-results-grid {
      display: flex;
      flex-direction: column;
      gap: 8px;
      max-height: 240px;
      overflow-y: auto;
      margin: 15px 0;
      padding-right: 5px;
    }

    .modal-result-row {
      background: rgba(17, 17, 27, 0.9);
      padding: 9px 12px;
      border-radius: 9px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 13px;
      border: 1px solid rgba(255,255,255,0.04);
    }
  </style>
</head>
<body>

  <h1>🥚 Eggs on the rock</h1>

  <!-- 상단 대시보드 -->
  <div class="stats-container">
    <div class="stat-item">💰 Gold: <span id="gold" class="stat-val">300</span></div>
    <div class="stat-item">⚡ CPS: <span id="cps" class="stat-val">0</span>/s</div>
    <div class="stat-item">🔄 Rebirth: <span id="reincarnations" class="stat-val">0</span></div>
    <button class="collection-open-btn" onclick="toggleCollectionModal(true)">📖 View Codex</button>
  </div>

  <!-- 알 선택 탭 -->
  <div class="egg-tabs">
    <button id="tab-egg1" class="tab-btn active" onclick="selectEgg('egg1')">🌱 Starter Egg</button>
    <button id="tab-egg2" class="tab-btn" onclick="selectEgg('egg2')" disabled>🌾 Grassland Egg🔒</button>
    <button id="tab-egg3" class="tab-btn" onclick="selectEgg('egg3')" disabled>🌊 Ocean Egg🔒</button>
    <button id="tab-egg4" class="tab-btn" onclick="selectEgg('egg4')" disabled>❄️ Arctic Egg🔒</button>
    <button id="tab-egg5" class="tab-btn" onclick="selectEgg('egg5')" disabled>🔥 Volcano Egg🔒</button>
    <button id="tab-egg6" class="tab-btn" onclick="selectEgg('egg6')" disabled>🌌 Cosmos Egg🔒</button>
  </div>

  <!-- 메인 알 부화 영역 -->
  <div class="egg-display-panel panel-egg1" id="egg-display-panel">
    <div class="theme-fx-layer" id="theme-fx-layer"></div>

    <h2 class="egg-title" id="egg-title">🌱 Starter Egg</h2>
    <div class="egg-cost-info" id="egg-cost-info">Cost per egg: 50 Gold (Farm Animals)</div>

    <div class="egg-drop-preview">
      <div class="egg-drop-preview-title">📊 Egg Drop Rates & Creatures</div>
      <div class="drop-list-grid" id="egg-drop-list"></div>
    </div>

    <div class="huge-egg-container" onclick="hatchCurrentEgg(1)">
      <div class="egg-effect-ring" id="egg-effect-ring"></div>
      <div id="huge-egg-svg" style="width:100%; height:100%; display:flex; justify-content:center; align-items:center;"></div>
    </div>

    <div class="hatch-btn-group">
      <button id="btn-hatch-1" onclick="hatchCurrentEgg(1)">Hatch 1</button>
      <button id="btn-hatch-2" onclick="hatchCurrentEgg(10)">Hatch 10</button>
      <button id="btn-hatch-5" onclick="hatchCurrentEgg(100)">Hatch 100</button>
      <button id="btn-hatch-10" onclick="hatchCurrentEgg(1000)">Hatch 1K🔥</button>
    </div>
  </div>

  <!-- 버튼 그룹 -->
  <button id="btn-auto" class="auto-btn" onclick="toggleAutoHatch()">⚡ Start Auto Hatching</button>
  <button id="btn-boss" class="boss-btn" onclick="startBossBattle()">⚔️ Challenge Theme Boss</button>
  <button class="test-cheat-btn" onclick="giveInfiniteGold()">🛠️ [Cheat] Infinite Gold</button>
  <button class="reincarnate-btn" onclick="reincarnate()">🌀 Rebirth (Req: 100,000 Gold)</button>

  <!-- 로그 -->
  <div class="log-box" id="log">
    <div>Welcome to Eggs on the rock! Hatch high-end eggs and collect mythical creatures.</div>
  </div>

  <!-- 도감 모달 -->
  <div class="collection-modal-overlay" id="collection-modal">
    <div class="collection-modal-content">
      <div class="collection-modal-header">
        <h2>📖 Codex Collection</h2>
        <button onclick="toggleCollectionModal(false)" style="padding: 6px 12px; background:linear-gradient(135deg, #f38ba8, #eba0ac); border:none; border-radius:8px; font-weight:bold; cursor:pointer;">Close ✖</button>
      </div>
      <div class="collection-list" id="collection-list"></div>
    </div>
  </div>

  <!-- 시네마틱 오버레이 -->
  <div class="cinematic-overlay" id="cinematic-overlay">
    <div class="cinematic-title" id="cinematic-title">🥚 Hatching egg...</div>
    <div class="cinematic-eggs-area" id="cinematic-area"></div>
  </div>

  <!-- 보스전 배틀 오버레이 -->
  <div class="boss-battle-overlay" id="boss-battle-overlay">
    <canvas id="boss-canvas"></canvas>

    <div class="cinematic-title" id="boss-battle-title" style="margin-bottom:5px; z-index:5;">⚔️ Boss Battle!</div>
    <div class="boss-timer-display" id="boss-timer-text">Time Left: 1:00</div>
    <div class="battle-arena" id="battle-arena">
      <div class="player-fighter" id="player-fighter" title="Your Army">🛡️</div>
      <div class="attack-beam" id="attack-beam"></div>
      <div style="font-size: 24px; color: #f9e2af; font-weight: bold; z-index: 5;">VS</div>
      <div class="boss-fighter" id="boss-fighter-icon"></div>
    </div>
    <div class="boss-hp-bar-container">
      <div class="boss-hp-bar" id="boss-hp-bar"></div>
    </div>
    <div id="boss-hp-text" style="font-size: 13px; color: #a6adc8; margin-top: 8px; z-index:5;">HP: 100%</div>

    <button class="boss-surrender-btn" onclick="surrenderBossBattle()">🏳️ Surrender Battle</button>
  </div>

  <!-- 결과 모달 -->
  <div class="modal-overlay" id="hatch-modal">
    <div class="modal-content">
      <h3 id="modal-title" style="margin:0; color: #89b4fa; font-size: 18px;">✨ Hatch Results</h3>
      <div class="modal-results-grid" id="modal-results"></div>
      <button onclick="closeModal()" style="width: 100%; padding: 11px; margin-top: 5px; border-radius:10px; font-weight:bold;">Confirm</button>
    </div>
  </div>

  <script>
    let state = {
      gold: 300,
      reincarnations: 0,
      multiplier: 1,
      unlockedCreatures: {},
      selectedEggKey: 'egg1',
      bossCleared: { egg1: false, egg2: false, egg3: false, egg4: false, egg5: false, egg6: false }
    };

    let isHatching = false;
    let isAutoHatching = false;
    let activeClockInterval = null;
    let activeBattleInterval = null;
    let activeCanvasAnimation = null;

    function giveInfiniteGold() {
      state.gold += 999999999999;
      log(`🛠️ <b>[Cheat]</b> Infinite gold added!`);
      updateUI();
    }

    const eggGraphics = {
      egg1: {
        svg: `<svg viewBox="0 0 100 100"><defs><linearGradient id="eg1" x1="0" y1="0" x2="1" y2="1"><stop offset="0%" stop-color="#fffbeb"/><stop offset="50%" stop-color="#fde047"/><stop offset="100%" stop-color="#ca8a04"/></linearGradient><filter id="glow1"><feDropShadow dx="0" dy="2" stdDeviation="3" flood-color="#facc15" flood-opacity="0.6"/></filter></defs><ellipse cx="50" cy="52" rx="34" ry="42" fill="url(#eg1)" filter="url(#glow1)" stroke="#fef08a" stroke-width="2.5"/><path d="M35,42 Q50,30 65,42 Q50,54 35,42 Z" fill="#ffffff" opacity="0.4"/><circle cx="50" cy="52" r="8" fill="#fef08a" opacity="0.8"/><ellipse cx="39" cy="34" rx="6" ry="12" fill="#ffffff" opacity="0.6" transform="rotate(-25 39 34)"/></svg>`,
        effectClass: 'effect-egg1'
      },
      egg2: {
        svg: `<svg viewBox="0 0 100 100"><defs><linearGradient id="eg2" x1="0" y1="0" x2="1" y2="1"><stop offset="0%" stop-color="#d9f99d"/><stop offset="50%" stop-color="#4ade80"/><stop offset="100%" stop-color="#166534"/></linearGradient><filter id="glow2"><feDropShadow dx="0" dy="2" stdDeviation="3" flood-color="#4ade80" flood-opacity="0.6"/></filter></defs><ellipse cx="50" cy="52" rx="34" ry="42" fill="url(#eg2)" filter="url(#glow2)" stroke="#bbf7d0" stroke-width="2.5"/><path d="M30,55 Q50,35 70,55" stroke="#ffffff" stroke-width="3" fill="none" opacity="0.6"/><path d="M35,45 Q50,25 65,45" stroke="#ffffff" stroke-width="2" fill="none" opacity="0.5"/><ellipse cx="39" cy="34" rx="6" ry="12" fill="#ffffff" opacity="0.6" transform="rotate(-25 39 34)"/></svg>`,
        effectClass: 'effect-egg2'
      },
      egg3: {
        svg: `<svg viewBox="0 0 100 100"><defs><linearGradient id="eg3" x1="0" y1="0" x2="1" y2="1"><stop offset="0%" stop-color="#bae6fd"/><stop offset="50%" stop-color="#38bdf8"/><stop offset="100%" stop-color="#1d4ed8"/></linearGradient><filter id="glow3"><feDropShadow dx="0" dy="2" stdDeviation="3" flood-color="#38bdf8" flood-opacity="0.6"/></filter></defs><ellipse cx="50" cy="52" rx="34" ry="42" fill="url(#eg3)" filter="url(#glow3)" stroke="#7dd3fc" stroke-width="2.5"/><path d="M26,45 Q50,30 74,45" stroke="#ffffff" stroke-width="3" fill="none" opacity="0.7"/><path d="M22,60 Q50,45 78,60" stroke="#ffffff" stroke-width="3" fill="none" opacity="0.7"/><circle cx="50" cy="30" r="3" fill="#ffffff"/><ellipse cx="39" cy="34" rx="6" ry="12" fill="#ffffff" opacity="0.6" transform="rotate(-25 39 34)"/></svg>`,
        effectClass: 'effect-egg3'
      },
      egg4: {
        svg: `<svg viewBox="0 0 100 100"><defs><linearGradient id="eg4" x1="0" y1="0" x2="1" y2="1"><stop offset="0%" stop-color="#f0fdf4"/><stop offset="50%" stop-color="#38bdf8"/><stop offset="100%" stop-color="#4f46e5"/></linearGradient><filter id="glow4"><feDropShadow dx="0" dy="2" stdDeviation="4" flood-color="#38bdf8" flood-opacity="0.7"/></filter></defs><ellipse cx="50" cy="52" rx="34" ry="42" fill="url(#eg4)" filter="url(#glow4)" stroke="#e0f2fe" stroke-width="2.5"/><path d="M32,36 L40,46 L32,56" stroke="#ffffff" stroke-width="3.5" fill="none" stroke-linecap="round"/><path d="M68,36 L60,46 L68,56" stroke="#ffffff" stroke-width="3.5" fill="none" stroke-linecap="round"/><polygon points="50,24 53,32 61,35 53,38 50,46 47,38 39,35 47,32" fill="#ffffff" opacity="0.9"/><ellipse cx="39" cy="34" rx="6" ry="12" fill="#ffffff" opacity="0.7" transform="rotate(-25 39 34)"/></svg>`,
        effectClass: 'effect-egg4'
      },
      egg5: {
        svg: `<svg viewBox="0 0 100 100"><defs><linearGradient id="eg5" x1="0" y1="0" x2="1" y2="1"><stop offset="0%" stop-color="#fef08a"/><stop offset="50%" stop-color="#f43f5e"/><stop offset="100%" stop-color="#7f1d1d"/></linearGradient><filter id="glow5"><feDropShadow dx="0" dy="2" stdDeviation="4" flood-color="#f43f5e" flood-opacity="0.8"/></filter></defs><ellipse cx="50" cy="52" rx="34" ry="42" fill="url(#eg5)" filter="url(#glow5)" stroke="#fca5a5" stroke-width="2.5"/><path d="M40,68 Q52,44 44,24 Q58,40 62,68 Z" fill="url(#fef08a)" opacity="0.9"/><circle cx="50" cy="32" r="4" fill="#ffffff"/><ellipse cx="39" cy="34" rx="6" ry="12" fill="#ffffff" opacity="0.6" transform="rotate(-25 39 34)"/></svg>`,
        effectClass: 'effect-egg5'
      },
      egg6: {
        svg: `<svg viewBox="0 0 100 100"><defs><linearGradient id="eg6" x1="0" y1="0" x2="1" y2="1"><stop offset="0%" stop-color="#e879f9"/><stop offset="50%" stop-color="#8b5cf6"/><stop offset="100%" stop-color="#030712"/></linearGradient><filter id="glow6"><feDropShadow dx="0" dy="2" stdDeviation="4" flood-color="#c084fc" flood-opacity="0.8"/></filter></defs><ellipse cx="50" cy="52" rx="34" ry="42" fill="url(#eg6)" filter="url(#glow6)" stroke="#d8b4fe" stroke-width="2.5"/><circle cx="32" cy="35" r="3" fill="#fef08a"/><circle cx="68" cy="48" r="3.5" fill="#38bdf8"/><path d="M34,55 Q50,40 66,55" stroke="#f472b6" stroke-width="3" fill="none" opacity="0.8"/><circle cx="50" cy="70" r="2.5" fill="#ffffff"/><ellipse cx="39" cy="34" rx="6" ry="12" fill="#ffffff" opacity="0.5" transform="rotate(-25 39 34)"/></svg>`,
        effectClass: 'effect-egg6'
      }
    };

    function makeBaseSVG(id, c1, c2, accent, innerShapeHTML) {
      return `<svg viewBox="0 0 100 100">
        <defs>
          <linearGradient id="grad_${id}" x1="0%" y1="0%" x2="100%" y2="100%">
            <stop offset="0%" stop-color="${c1}"/>
            <stop offset="50%" stop-color="${c2}"/>
            <stop offset="100%" stop-color="${accent}"/>
          </linearGradient>
          <filter id="glow_${id}" x="-30%" y="-30%" width="160%" height="160%">
            <feGaussianBlur stdDeviation="2.5" result="blur" />
            <feComposite in="SourceGraphic" in2="blur" operator="over"/>
          </filter>
        </defs>
        <g filter="url(#glow_${id})">
          <circle cx="50" cy="50" r="38" fill="${accent}" opacity="0.18"/>
          ${innerShapeHTML}
        </g>
      </svg>`;
    }

    const graphics = {
      chick: makeBaseSVG('c1', '#f9e2af', '#eed49f', '#fab387', `<circle cx="50" cy="55" r="24" fill="url(#grad_c1)" stroke="#fab387" stroke-width="2.5"/><circle cx="42" cy="48" r="3" fill="#181825"/><circle cx="58" cy="48" r="3" fill="#181825"/><polygon points="47,52 53,52 50,58" fill="#f5a97f"/><path d="M46,31 Q50,20 54,31" stroke="#f9e2af" stroke-width="3" stroke-linecap="round" fill="none"/>`),
      sheep: makeBaseSVG('c2', '#cad3f5', '#b7bdf8', '#ffffff', `<ellipse cx="50" cy="58" rx="26" ry="18" fill="url(#grad_c2)" stroke="#ffffff" stroke-width="2"/><circle cx="50" cy="42" r="14" fill="#ffffff" stroke="#b7bdf8" stroke-width="2"/><circle cx="44" cy="40" r="2.5" fill="#181825"/><circle cx="56" cy="40" r="2.5" fill="#181825"/><polygon points="50,44 47,47 53,47" fill="#ee99a0"/>`),
      cow: makeBaseSVG('c3', '#ffffff', '#b4befe', '#f5bde6', `<rect x="25" y="38" width="50" height="32" rx="10" fill="url(#grad_c3)" stroke="#45475a" stroke-width="2.5"/><path d="M32,38 Q38,38 38,48 Q30,52 30,38 Z" fill="#181825"/><circle cx="40" cy="45" r="2.5" fill="#181825"/><circle cx="60" cy="45" r="2.5" fill="#181825"/><polygon points="32,30 24,25 34,35" fill="#eed49f"/><polygon points="68,30 76,25 66,35" fill="#eed49f"/>`),
      alpaca: makeBaseSVG('c4', '#f5e0dc', '#f2cdcd', '#c6a0f6', `<rect x="42" y="40" width="16" height="32" rx="8" fill="url(#grad_c4)" stroke="#c6a0f6" stroke-width="2"/><circle cx="50" cy="32" r="13" fill="url(#grad_c4)"/><circle cx="45" cy="30" r="2.5" fill="#181825"/><circle cx="55" cy="30" r="2.5" fill="#181825"/><polygon points="50,34 47,37 53,37" fill="#f38ba8"/>`),
      goose: makeBaseSVG('c5', '#ffffff', '#e0def4', '#f5a97f', `<path d="M28,62 Q28,40 50,35 Q65,45 72,62 Z" fill="url(#grad_c5)" stroke="#e0def4" stroke-width="2"/><path d="M50,35 Q60,22 58,12" stroke="#ffffff" stroke-width="10" stroke-linecap="round" fill="none"/><polygon points="58,10 74,15 60,19" fill="#f5a97f"/><circle cx="54" cy="13" r="2" fill="#181825"/>`),
      mythical_starter: makeBaseSVG('c6', '#f9e2af', '#f5e0dc', '#fab387', `<ellipse cx="50" cy="56" rx="22" ry="16" fill="url(#grad_c6)" stroke="#fab387" stroke-width="2.5"/><circle cx="64" cy="44" r="11" fill="url(#grad_c6)"/><path d="M35,46 Q15,18 26,52 Z" fill="#f5e0dc" stroke="#fab387" stroke-width="2"/><circle cx="68" cy="42" r="2.5" fill="#181825"/><path d="M45,20 L50,10 L55,20" stroke="#f9e2af" stroke-width="3" fill="none"/>`),

      pegasus: (() => {
        return `<svg viewBox="0 0 100 100">
          <defs>
            <linearGradient id="rainbow_grad" x1="0%" y1="0%" x2="100%" y2="100%"><stop offset="0%" stop-color="#ff7675"/><stop offset="20%" stop-color="#fab387"/><stop offset="40%" stop-color="#f9e2af"/><stop offset="60%" stop-color="#a6e3a1"/><stop offset="80%" stop-color="#89b4fa"/><stop offset="100%" stop-color="#cba6f7"/></linearGradient>
            <filter id="glow_peg" x="-30%" y="-30%" width="160%" height="160%"><feGaussianBlur stdDeviation="3" result="blur" /><feComposite in="SourceGraphic" in2="blur" operator="over"/></filter>
          </defs>
          <g filter="url(#glow_peg)">
            <circle cx="50" cy="50" r="38" fill="#cba6f7" opacity="0.25"/>
            <ellipse cx="50" cy="56" rx="22" ry="16" fill="url(#rainbow_grad)" stroke="#ffffff" stroke-width="2"/>
            <path d="M38,40 Q15,15 28,50 Q20,30 38,45 Z" fill="url(#rainbow_grad)" stroke="#ffffff" stroke-width="1.5"/>
            <circle cx="68" cy="42" r="2.5" fill="#11111b"/>
            <path d="M64,30 Q72,15 78,30 Z" fill="#cba6f7"/>
            <polygon points="50,22 53,8 56,22" fill="#ffffff" stroke="#f9e2af" stroke-width="1.5"/>
          </g>
        </svg>`;
      })(),

      rabbit: makeBaseSVG('c8', '#f5e0dc', '#f2cdcd', '#f38ba8', `<ellipse cx="50" cy="60" rx="20" ry="16" fill="url(#grad_c8)" stroke="#f38ba8" stroke-width="2"/><circle cx="50" cy="46" r="14" fill="url(#grad_c8)"/><path d="M42,32 Q36,8 44,26 M58,32 Q64,8 56,26" stroke="#f5e0dc" stroke-width="6" stroke-linecap="round" fill="none"/><circle cx="44" cy="44" r="2" fill="#181825"/><circle cx="56" cy="44" r="2" fill="#181825"/>`),
      zebra: makeBaseSVG('c9', '#ffffff', '#e2e8f0', '#1e293b', `<rect x="28" y="38" width="44" height="26" rx="8" fill="url(#grad_c9)" stroke="#1e293b" stroke-width="2"/><path d="M34,38 L38,64 M42,38 L46,64 M50,38 L54,64 M58,38 L62,64" stroke="#1e293b" stroke-width="3.5" stroke-linecap="round"/><circle cx="66" cy="38" r="11" fill="#ffffff" stroke="#1e293b" stroke-width="2"/><path d="M60,32 L66,20 L72,32 Z" fill="#1e293b"/><circle cx="70" cy="36" r="2" fill="#1e293b"/><rect x="33" y="64" width="4" height="12" fill="#1e293b"/><rect x="59" y="64" width="4" height="12" fill="#1e293b"/>`),
      kangaroo: makeBaseSVG('c10', '#f5a97f', '#ee99a0', '#f9e2af', `<ellipse cx="48" cy="58" rx="18" ry="22" fill="url(#grad_c10)" stroke="#ee99a0" stroke-width="2"/><circle cx="58" cy="36" r="12" fill="url(#grad_c10)"/><path d="M53,26 L56,12 L60,26 Z" fill="url(#grad_c10)"/><circle cx="62" cy="34" r="2.5" fill="#181825"/>`),
      cheetah: makeBaseSVG('c11', '#f5a97f', '#e8a07a', '#f9e2af', `<ellipse cx="48" cy="58" rx="24" ry="15" fill="url(#grad_c11)" stroke="#e8a07a" stroke-width="2"/><circle cx="68" cy="45" r="10" fill="url(#grad_c11)"/><circle cx="42" cy="55" r="2" fill="#181825"/><circle cx="54" cy="52" r="2" fill="#181825"/><circle cx="72" cy="42" r="2" fill="#181825"/>`),
      lion: makeBaseSVG('c12', '#e8a07a', '#f5a97f', '#f9e2af', `<circle cx="50" cy="50" r="26" fill="url(#grad_c12)" stroke="#fab387" stroke-width="2.5"/><circle cx="50" cy="50" r="16" fill="#f5a97f"/><circle cx="43" cy="46" r="2.5" fill="#181825"/><circle cx="57" cy="46" r="2.5" fill="#181825"/><polygon points="50,50 46,54 54,54" fill="#181825"/>`),
      mythical_grass: makeBaseSVG('c13', '#ffffff', '#e0f2fe', '#0284c7', `<ellipse cx="48" cy="56" rx="24" ry="15" fill="url(#grad_c13)" stroke="#0284c7" stroke-width="2.5"/><path d="M38,42 L41,68 M47,40 L50,70 M56,42 L59,68" stroke="#0284c7" stroke-width="3.5" stroke-linecap="round"/><circle cx="68" cy="44" r="11" fill="#ffffff" stroke="#0284c7" stroke-width="2"/><circle cx="72" cy="42" r="2.5" fill="#0284c7"/><polygon points="63,30 66,22 69,30 72,22 75,30" fill="#f59e0b"/>`),

      whitetiger: (() => {
        return `<svg viewBox="0 0 100 100">
          <defs>
            <linearGradient id="neon_lion_grad" x1="0%" y1="0%" x2="100%" y2="100%"><stop offset="0%" stop-color="#ff007f"/><stop offset="50%" stop-color="#9b5de5"/><stop offset="100%" stop-color="#00f5d4"/></linearGradient>
            <filter id="neon_glow" x="-50%" y="-50%" width="200%" height="200%"><feGaussianBlur stdDeviation="4" result="blur" /><feComposite in="SourceGraphic" in2="blur" operator="over"/></filter>
          </defs>
          <g filter="url(#neon_glow)">
            <ellipse cx="48" cy="56" rx="24" ry="15" fill="#11111b" stroke="url(#neon_lion_grad)" stroke-width="3"/>
            <circle cx="68" cy="44" r="12" fill="#11111b" stroke="url(#neon_lion_grad)" stroke-width="3"/>
            <path d="M52,28 Q68,6 86,28 Q75,50 85,62 Z" fill="url(#neon_lion_grad)" opacity="0.75"/>
            <circle cx="72" cy="42" r="3.5" fill="#00f5d4"/>
          </g>
        </svg>`;
      })(),

      fish: makeBaseSVG('c15', '#89dceb', '#74c7ec', '#f5a97f', `<ellipse cx="44" cy="50" rx="22" ry="15" fill="url(#grad_c15)" stroke="#74c7ec" stroke-width="2"/><polygon points="66,50 86,34 82,50 86,66" fill="#f5a97f"/><circle cx="34" cy="46" r="3" fill="#181825"/>`),
      dolphin: makeBaseSVG('c16', '#89b4fa', '#74c7ec', '#ffffff', `<path d="M16,60 Q45,18 82,48 Q58,64 38,56 Z" fill="url(#grad_c16)" stroke="#74c7ec" stroke-width="2"/><polygon points="44,36 54,20 50,38" fill="url(#grad_c16)"/><circle cx="70" cy="42" r="2.5" fill="#181825"/>`),
      seaturtle: makeBaseSVG('c17', '#a6e3a1', '#8ad48b', '#f9e2af', `<ellipse cx="50" cy="54" rx="20" ry="16" fill="url(#grad_c17)" stroke="#8ad48b" stroke-width="2.5"/><circle cx="50" cy="34" r="7" fill="url(#grad_c17)"/><polygon points="50,42 42,50 50,58 58,50" fill="#f9e2af"/><circle cx="47" cy="32" r="1.5" fill="#181825"/><circle cx="53" cy="32" r="1.5" fill="#181825"/>`),
      octopus: makeBaseSVG('c18', '#cba6f7', '#b4befe', '#f38ba8', `<circle cx="50" cy="42" r="18" fill="url(#grad_c18)" stroke="#b4befe" stroke-width="2.5"/><path d="M34,56 Q28,84 36,88 M42,58 Q38,86 46,86 M54,58 Q62,86 54,86 M66,56 Q72,84 64,88" stroke="#cba6f7" stroke-width="5" stroke-linecap="round" fill="none"/><circle cx="43" cy="38" r="2.5" fill="#181825"/><circle cx="57" cy="38" r="2.5" fill="#181825"/>`),
      shark: makeBaseSVG('c19', '#6e738d', '#89b4fa', '#f9e2af', `<path d="M18,54 Q50,18 85,48 Q50,68 18,54 Z" fill="url(#grad_c19)" stroke="#89b4fa" stroke-width="2"/><polygon points="46,34 56,14 52,36" fill="url(#grad_c19)"/><circle cx="72" cy="42" r="2.5" fill="#181825"/>`),
      kraken: makeBaseSVG('c20', '#363a4f', '#cba6f7', '#eed49f', `<circle cx="50" cy="40" r="20" fill="url(#grad_c20)" stroke="#cba6f7" stroke-width="2.5"/><path d="M30,54 Q20,84 32,88 M42,56 Q36,88 46,88 M54,56 Q64,88 54,88 M70,54 Q80,84 68,88" stroke="#cba6f7" stroke-width="6" stroke-linecap="round" fill="none"/><circle cx="42" cy="36" r="3" fill="#eed49f"/><circle cx="58" cy="36" r="3" fill="#eed49f"/>`),

      leviathan: (() => {
        return `<svg viewBox="0 0 100 100">
          <defs>
            <linearGradient id="deep_purple_grad" x1="0%" y1="0%" x2="100%" y2="100%"><stop offset="0%" stop-color="#4a0e4e"/><stop offset="50%" stop-color="#7b1fa2"/><stop offset="100%" stop-color="#b388ff"/></linearGradient>
            <filter id="glow_lev" x="-30%" y="-30%" width="160%" height="160%"><feGaussianBlur stdDeviation="3" result="blur" /><feComposite in="SourceGraphic" in2="blur" operator="over"/></filter>
          </defs>
          <g filter="url(#glow_lev)">
            <path d="M12,58 Q38,20 74,46 Q88,56 92,50 Q96,44 88,40 Q80,36 74,40 Q50,18 24,48 Z" fill="url(#deep_purple_grad)" stroke="#e1bee7" stroke-width="2.5"/>
            <path d="M36,40 Q50,10 64,36" stroke="#e1bee7" stroke-width="4" fill="none" stroke-linecap="round"/>
            <path d="M72,40 L88,24 L82,44 Z" fill="#e1bee7"/>
            <circle cx="76" cy="40" r="3.5" fill="#ff4081"/>
          </g>
        </svg>`;
      })(),

      penguin: makeBaseSVG('c22', '#363a4f', '#89b4fa', '#fab387', `<ellipse cx="50" cy="56" rx="18" ry="22" fill="url(#grad_c22)" stroke="#89b4fa" stroke-width="2"/><ellipse cx="50" cy="58" rx="12" ry="16" fill="#ffffff"/><circle cx="43" cy="45" r="2" fill="#181825"/><circle cx="57" cy="45" r="2" fill="#181825"/><polygon points="50,49 46,53 54,53" fill="#fab387"/>`),
      seal: makeBaseSVG('c23', '#a5adcb', '#b4befe', '#ffffff', `<ellipse cx="50" cy="60" rx="24" ry="15" fill="url(#grad_c23)" stroke="#b4befe" stroke-width="2"/><circle cx="68" cy="50" r="10" fill="url(#grad_c23)"/><circle cx="73" cy="47" r="2" fill="#181825"/>`),
      polarbear: makeBaseSVG('c24', '#ffffff', '#cbd5e1', '#64748b', `<rect x="26" y="38" width="48" height="30" rx="12" fill="url(#grad_c24)" stroke="#cbd5e1" stroke-width="2.5"/><circle cx="66" cy="44" r="12" fill="#ffffff" stroke="#cbd5e1" stroke-width="2"/><circle cx="72" cy="42" r="2" fill="#1e293b"/><ellipse cx="74" cy="46" rx="3" ry="2" fill="#1e293b"/><circle cx="58" cy="28" r="3" fill="#ffffff" stroke="#cbd5e1" stroke-width="1.5"/><circle cx="72" cy="28" r="3" fill="#ffffff" stroke="#cbd5e1" stroke-width="1.5"/>`),
      aurorafox: makeBaseSVG('c25', '#2dd4bf', '#a855f7', '#38bdf8', `<ellipse cx="46" cy="58" rx="20" ry="15" fill="url(#grad_c25)" stroke="#38bdf8" stroke-width="2"/><circle cx="62" cy="44" r="10" fill="#2dd4bf" stroke="#38bdf8" stroke-width="2"/><path d="M54,34 L60,18 L66,34 Z" fill="#2dd4bf"/><circle cx="66" cy="42" r="2" fill="#111827"/><path d="M28,62 Q10,50 22,35 Q35,45 30,60 Z" fill="#a855f7" opacity="0.8"/>`),
      yeti: makeBaseSVG('c26', '#f8fafc', '#94a3b8', '#0284c7', `<rect x="28" y="32" width="44" height="40" rx="14" fill="url(#grad_c26)" stroke="#0284c7" stroke-width="2.5"/><circle cx="40" cy="46" r="3" fill="#0f172a"/><circle cx="60" cy="46" r="3" fill="#0f172a"/><path d="M42,56 L58,56 L50,64 Z" fill="#0f172a"/><polygon points="46,32 50,16 54,32" fill="#38bdf8" stroke="#bae6fd" stroke-width="1"/>`),
      mythical_arctic: makeBaseSVG('c27', '#89dceb', '#b4befe', '#ffffff', `<circle cx="50" cy="50" r="24" fill="url(#grad_c27)" stroke="#ffffff" stroke-width="2.5"/><path d="M36,36 L50,22 L64,36" stroke="#ffffff" stroke-width="3.5" fill="none"/><circle cx="42" cy="48" r="2.5" fill="#181825"/><circle cx="58" cy="48" r="2.5" fill="#181825"/>`),
      frostdragon: makeBaseSVG('c28', '#38bdf8', '#0284c7', '#e0f2fe', `<path d="M18,58 Q50,20 84,52 Q50,72 18,58 Z" fill="url(#grad_c28)" stroke="#bae6fd" stroke-width="2.5"/><path d="M64,40 L78,20 L72,44 Z" fill="#bae6fd"/><circle cx="72" cy="40" r="3.5" fill="#f43f5e"/><path d="M40,46 L30,26 M50,42 L55,22" stroke="#e0f2fe" stroke-width="2" stroke-linecap="round"/>`),
      lavalizard: makeBaseSVG('c29', '#f97316', '#dc2626', '#fde047', `<ellipse cx="48" cy="58" rx="22" ry="14" fill="url(#grad_c29)" stroke="#fde047" stroke-width="2"/><circle cx="68" cy="46" r="9" fill="#dc2626" stroke="#fde047" stroke-width="1.5"/><circle cx="72" cy="44" r="2" fill="#fde047"/><path d="M36,52 L42,58 M48,50 L52,56" stroke="#fde047" stroke-width="2.5" stroke-linecap="round"/>`),
      flamesprite: makeBaseSVG('c30', '#fab387', '#f38ba8', '#f9e2af', `<path d="M50,22 Q64,46 56,68 Q50,78 44,68 Q36,46 50,22 Z" fill="url(#grad_c30)" stroke="#f38ba8" stroke-width="2"/><circle cx="45" cy="52" r="2" fill="#181825"/><circle cx="55" cy="52" r="2" fill="#181825"/>`),
      magmaturtle: makeBaseSVG('c31', '#ea580c', '#9a3412', '#facc15', `<ellipse cx="50" cy="56" rx="22" ry="17" fill="url(#grad_c31)" stroke="#facc15" stroke-width="2.5"/><circle cx="50" cy="32" r="8" fill="#9a3412" stroke="#ea580c" stroke-width="2"/><path d="M42,52 Q50,44 58,52 M46,62 Q50,56 54,62" stroke="#facc15" stroke-width="2.5" fill="none"/><circle cx="47" cy="30" r="1.5" fill="#facc15"/><circle cx="53" cy="30" r="1.5" fill="#facc15"/>`),
      phoenix: makeBaseSVG('c32', '#f97316', '#e11d48', '#facc15', `<path d="M22,60 Q50,25 78,60 Q50,78 22,60 Z" fill="url(#grad_c32)" stroke="#facc15" stroke-width="2"/><path d="M35,42 Q15,15 28,52 Q18,30 35,48 Z" fill="#facc15" stroke="#f97316" stroke-width="1.5"/><path d="M65,42 Q85,15 72,52 Q82,30 65,48 Z" fill="#facc15" stroke="#f97316" stroke-width="1.5"/><circle cx="50" cy="36" r="4" fill="#fde047"/>`),
      magmadragon: makeBaseSVG('c33', '#dc2626', '#7f1d1d', '#fbbf24', `<path d="M18,56 Q50,18 86,52 Q50,72 18,56 Z" fill="url(#grad_c33)" stroke="#fbbf24" stroke-width="2.5"/><path d="M44,38 Q30,12 60,32 Z" fill="#fbbf24" stroke="#f87171" stroke-width="1.5"/><path d="M70,38 L82,18 L76,42 Z" fill="#fbbf24"/><circle cx="74" cy="38" r="3" fill="#fde047"/>`),
      mythical_volcano: makeBaseSVG('c34', '#fab387', '#f38ba8', '#f9e2af', `<circle cx="50" cy="50" r="24" fill="url(#grad_c34)" stroke="#fab387" stroke-width="2.5"/><polygon points="50,24 54,36 68,40 56,50 60,66 50,56 40,66 44,50 32,40 46,36" fill="#f9e2af"/><circle cx="44" cy="46" r="2.5" fill="#181825"/><circle cx="56" cy="46" r="2.5" fill="#181825"/>`),
      ifrit: makeBaseSVG('c35', '#f38ba8', '#fab387', '#f9e2af', `<circle cx="50" cy="40" r="18" fill="url(#grad_c35)" stroke="#f9e2af" stroke-width="2.5"/><path d="M32,54 Q22,82 34,86 M50,54 L50,86 M68,54 Q78,82 66,86" stroke="#fab387" stroke-width="5" fill="none" stroke-linecap="round"/><circle cx="42" cy="38" r="3" fill="#f9e2af"/><circle cx="58" cy="38" r="3" fill="#f9e2af"/>`),
      stargelly: makeBaseSVG('c36', '#cba6f7', '#b4befe', '#f9e2af', `<ellipse cx="50" cy="48" rx="20" ry="16" fill="url(#grad_c36)" stroke="#b4befe" stroke-width="2"/><path d="M36,54 L34,72 M43,54 L43,75 M57,54 L57,75 M64,54 L66,72" stroke="#b4befe" stroke-width="2.5" stroke-linecap="round"/><circle cx="42" cy="45" r="2" fill="#f9e2af"/><circle cx="58" cy="45" r="2" fill="#f9e2af"/>`),
      alien: makeBaseSVG('c37', '#a6e3a1', '#74c7ec', '#f5c2e7', `<ellipse cx="50" cy="58" rx="16" ry="20" fill="url(#grad_c37)" stroke="#94e2d5" stroke-width="2"/><circle cx="50" cy="36" r="12" fill="url(#grad_c37)"/><ellipse cx="44" cy="34" rx="3.5" ry="5" fill="#181825"/><ellipse cx="56" cy="34" rx="3.5" ry="5" fill="#181825"/><ellipse cx="50" cy="68" rx="22" ry="6" fill="#74c7ec" opacity="0.8"/>`),
      meteorsnipe: makeBaseSVG('c38', '#f59e0b', '#ef4444', '#a855f7', `<ellipse cx="46" cy="58" rx="22" ry="14" fill="url(#grad_c38)" stroke="#fde047" stroke-width="2"/><circle cx="66" cy="46" r="10" fill="#ef4444" stroke="#fde047" stroke-width="2"/><path d="M12,62 Q30,55 24,45" stroke="#38bdf8" stroke-width="4" stroke-linecap="round" fill="none"/><circle cx="70" cy="44" r="2" fill="#fde047"/>`),
      nebulapegasus: makeBaseSVG('c39', '#8b5cf6', '#3b82f6', '#ec4899', `<ellipse cx="50" cy="56" rx="20" ry="15" fill="url(#grad_c39)" stroke="#ec4899" stroke-width="2.5"/><circle cx="64" cy="44" r="10" fill="#8b5cf6" stroke="#3b82f6" stroke-width="2"/><path d="M38,40 Q15,15 26,48 Q20,28 38,44 Z" fill="#ec4899" stroke="#38bdf8" stroke-width="1.5"/><circle cx="68" cy="42" r="2.5" fill="#f9e2af"/><polygon points="50,22 53,10 56,22" fill="#38bdf8"/>`),
      blackholekraken: makeBaseSVG('c40', '#181825', '#cba6f7', '#f9e2af', `<circle cx="50" cy="38" r="20" fill="url(#grad_c40)" stroke="#cba6f7" stroke-width="2.5"/><path d="M30,52 Q20,82 32,86 M40,54 L42,86 M58,54 L58,86 M70,52 Q80,82 68,86" stroke="#89b4fa" stroke-width="6" stroke-linecap="round" fill="none"/><circle cx="42" cy="35" r="3.5" fill="#f9e2af"/><circle cx="58" cy="35" r="3.5" fill="#f9e2af"/>`),
      mythical_cosmos: makeBaseSVG('c41', '#313244', '#cba6f7', '#f9e2af', `<circle cx="50" cy="50" r="24" fill="url(#grad_c41)" stroke="#f9e2af" stroke-width="2.5"/><circle cx="50" cy="50" r="16" fill="#f9e2af" opacity="0.3"/><circle cx="42" cy="48" r="2.5" fill="#ffffff"/><circle cx="58" cy="48" r="2.5" fill="#ffffff"/><path d="M36,60 Q50,72 64,60" stroke="#ffffff" stroke-width="2.5" fill="none"/>`),
      cosmicleviathan: makeBaseSVG('c42', '#cba6f7', '#b4befe', '#f9e2af', `<path d="M12,58 Q38,20 74,46 Q88,56 92,50 Q96,44 88,40 Q80,36 74,40 Q50,18 24,48 Z" fill="url(#grad_c42)" stroke="#f9e2af" stroke-width="2.5"/><path d="M36,40 Q50,10 64,36" stroke="#f9e2af" stroke-width="4" fill="none" stroke-linecap="round"/><path d="M72,40 L88,24 L82,44 Z" fill="url(#grad_c42)"/><circle cx="76" cy="40" r="3.5" fill="#f9e2af"/>`),

      // 보스 1~6
      boss1: makeBaseSVG('b1', '#2ecc71', '#27ae60', '#f1c40f', `
        <defs>
          <linearGradient id="golem_body" x1="0" y1="0" x2="1" y2="1"><stop offset="0%" stop-color="#34495e"/><stop offset="50%" stop-color="#27ae60"/><stop offset="100%" stop-color="#1e272c"/></linearGradient>
          <filter id="golem_glow"><feGaussianBlur stdDeviation="3" result="b"/><feComposite in="SourceGraphic" in2="b" operator="over"/></filter>
        </defs>
        <rect x="10" y="36" width="22" height="32" rx="8" fill="#34495e" stroke="#2ecc71" stroke-width="3"/>
        <rect x="68" y="36" width="22" height="32" rx="8" fill="#34495e" stroke="#2ecc71" stroke-width="3"/>
        <rect x="24" y="28" width="52" height="46" rx="10" fill="url(#golem_body)" stroke="#2ecc71" stroke-width="3"/>
        <rect x="36" y="12" width="28" height="22" rx="6" fill="#2c3e50" stroke="#2ecc71" stroke-width="2.5"/>
        <path d="M38,12 Q50,0 62,12" fill="none" stroke="#2ecc71" stroke-width="4" stroke-linecap="round"/>
        <circle cx="50" cy="6" r="4" fill="#f1c40f" filter="url(#golem_glow)"/>
        <circle cx="50" cy="51" r="10" fill="#f1c40f" filter="url(#golem_glow)" stroke="#ffffff" stroke-width="2"/>
        <circle cx="43" cy="22" r="2.5" fill="#00ffcc" filter="url(#golem_glow)"/>
        <circle cx="57" cy="22" r="2.5" fill="#00ffcc" filter="url(#golem_glow)"/>
      `),

      boss2: makeBaseSVG('b2', '#f39c12', '#e67e22', '#9b59b6', `
        <defs>
          <linearGradient id="lion_body_grad" x1="0" y1="0" x2="1" y2="1"><stop offset="0%" stop-color="#f1c40f"/><stop offset="50%" stop-color="#e67e22"/><stop offset="100%" stop-color="#8e44ad"/></linearGradient>
          <filter id="lion_glow"><feGaussianBlur stdDeviation="3" result="b"/><feComposite in="SourceGraphic" in2="b" operator="over"/></filter>
        </defs>
        <ellipse cx="50" cy="62" rx="26" ry="18" fill="url(#lion_body_grad)" stroke="#f1c40f" stroke-width="2.5"/>
        <rect x="34" y="70" width="8" height="15" rx="4" fill="#d35400"/>
        <rect x="58" y="70" width="8" height="15" rx="4" fill="#d35400"/>
        <circle cx="50" cy="42" r="26" fill="url(#lion_body_grad)" stroke="#ffffff" stroke-width="2" opacity="0.9"/>
        <circle cx="50" cy="42" r="15" fill="#d35400" stroke="#f1c40f" stroke-width="2"/>
        <polygon points="50,20 42,8 50,14 58,8" fill="#f1c40f" stroke="#ffffff" stroke-width="1.5"/>
        <circle cx="44" cy="40" r="3" fill="#00ffff" filter="url(#lion_glow)"/>
        <circle cx="56" cy="40" r="3" fill="#ff007f" filter="url(#lion_glow)"/>
      `),

      boss3: makeBaseSVG('b3', '#48dbfb', '#0abde3', '#10ac84', `
        <path d="M12,56 Q45,22 88,44 L78,62 Q45,74 12,56 Z" fill="#0abde3" stroke="#48dbfb" stroke-width="2.5"/>
        <polygon points="46,34 58,10 52,38" fill="#48dbfb"/>
        <circle cx="70" cy="42" r="3" fill="#ff5252"/>
      `),

      boss4: makeBaseSVG('b4', '#00cec9', '#0984e3', '#ffffff', `
        <defs>
          <linearGradient id="frost_wyvern" x1="0" y1="0" x2="1" y2="1"><stop offset="0%" stop-color="#ffffff"/><stop offset="50%" stop-color="#74b9ff"/><stop offset="100%" stop-color="#0984e3"/></linearGradient>
          <filter id="wyvern_glow"><feGaussianBlur stdDeviation="3" result="b"/><feComposite in="SourceGraphic" in2="b" operator="over"/></filter>
        </defs>
        <path d="M30,42 L8,14 L24,48 L4,32 L32,60 Z" fill="url(#frost_wyvern)" stroke="#ffffff" stroke-width="2"/>
        <path d="M70,42 L92,14 L76,48 L96,32 L68,60 Z" fill="url(#frost_wyvern)" stroke="#ffffff" stroke-width="2"/>
        <ellipse cx="50" cy="58" rx="20" ry="16" fill="url(#frost_wyvern)" stroke="#ffffff" stroke-width="2"/>
        <path d="M50,70 Q50,92 70,88" stroke="url(#frost_wyvern)" stroke-width="8" stroke-linecap="round" fill="none"/>
        <circle cx="50" cy="35" r="13" fill="#0984e3" stroke="#ffffff" stroke-width="2.5"/>
        <polygon points="50,22 43,8 47,22" fill="#ffffff"/><polygon points="50,22 57,8 53,22" fill="#ffffff"/>
        <circle cx="45" cy="33" r="2.5" fill="#ff7675" filter="url(#wyvern_glow)"/>
        <circle cx="55" cy="33" r="2.5" fill="#ff7675" filter="url(#wyvern_glow)"/>
      `),

      boss5: makeBaseSVG('b5', '#ff3838', '#ea580c', '#facc15', `
        <defs>
          <linearGradient id="magma_turtle_shell" x1="0" y1="0" x2="1" y2="1"><stop offset="0%" stop-color="#7f1d1d"/><stop offset="50%" stop-color="#ea580c"/><stop offset="100%" stop-color="#1c1917"/></linearGradient>
          <filter id="lava_glow"><feGaussianBlur stdDeviation="3.5" result="b"/><feComposite in="SourceGraphic" in2="b" operator="over"/></filter>
        </defs>
        <rect x="18" y="58" width="14" height="20" rx="6" fill="#1c1917" stroke="#ea580c" stroke-width="2"/>
        <rect x="68" y="58" width="14" height="20" rx="6" fill="#1c1917" stroke="#ea580c" stroke-width="2"/>
        <rect x="24" y="28" width="12" height="18" rx="5" fill="#1c1917" stroke="#ea580c" stroke-width="2"/>
        <rect x="64" y="28" width="12" height="18" rx="5" fill="#1c1917" stroke="#ea580c" stroke-width="2"/>
        <ellipse cx="50" cy="52" rx="30" ry="24" fill="url(#magma_turtle_shell)" stroke="#facc15" stroke-width="3"/>
        <path d="M50,32 Q38,48 50,68 M32,50 Q50,54 68,50" stroke="#facc15" stroke-width="3.5" fill="none" stroke-linecap="round" filter="url(#lava_glow)"/>
        <circle cx="50" cy="50" r="7" fill="#ff3838" filter="url(#lava_glow)"/>
        <ellipse cx="50" cy="24" rx="12" ry="10" fill="#1c1917" stroke="#ff3838" stroke-width="2.5"/>
        <circle cx="44" cy="22" r="2.5" fill="#facc15" filter="url(#lava_glow)"/>
        <circle cx="56" cy="22" r="2.5" fill="#facc15" filter="url(#lava_glow)"/>
      `),

      boss6: makeBaseSVG('b6', '#8e44ad', '#3498db', '#f1c40f', `
        <defs>
          <linearGradient id="cosmic_lev_body" x1="0" y1="0" x2="1" y2="1"><stop offset="0%" stop-color="#9b59b6"/><stop offset="50%" stop-color="#2980b9"/><stop offset="100%" stop-color="#0f172a"/></linearGradient>
          <filter id="cosmic_lev_glow"><feGaussianBlur stdDeviation="4" result="b"/><feComposite in="SourceGraphic" in2="b" operator="over"/></filter>
        </defs>
        <path d="M10,58 Q35,16 76,42 Q92,52 96,42 Q100,32 86,30 Q72,28 66,32 Q42,10 16,46 Z" fill="url(#cosmic_lev_body)" stroke="#ffffff" stroke-width="3" filter="url(#cosmic_lev_glow)"/>
        <path d="M36,36 Q54,8 66,32" stroke="#f1c40f" stroke-width="4.5" fill="none" stroke-linecap="round"/>
        <polygon points="70,36 90,18 82,42" fill="#ffffff" stroke="#9b59b6" stroke-width="2"/>
        <circle cx="76" cy="35" r="4.5" fill="#ff007f" filter="url(#cosmic_lev_glow)"/>
        <circle cx="76" cy="35" r="1.5" fill="#ffffff"/>
        <circle cx="30" cy="45" r="2" fill="#ffffff"/><circle cx="50" cy="25" r="2.5" fill="#f1c40f"/><circle cx="65" cy="48" r="2" fill="#38bdf8"/>
      `)
    };

    const eggs = {
      egg1: {
        title: '🌱 Starter Egg',
        desc: 'Cost per egg: 50 Gold (Farm Animals)',
        cost: 50,
        reqRebirths: 0,
        bossName: 'Titan Nature Golem',
        bossGraphic: graphics.boss1,
        graphic: eggGraphics.egg1,
        panelClass: 'panel-egg1',
        pool: [
          { id: 'c1', name: 'Chick', rarity: 'Common', weight: 4500, income: 1, svg: graphics.chick },
          { id: 'c2', name: 'Fluffy Sheep', rarity: 'Uncommon', weight: 3000, income: 3, svg: graphics.sheep },
          { id: 'c3', name: 'Spotty Cow', rarity: 'Rare', weight: 1500, income: 6, svg: graphics.cow },
          { id: 'c4', name: 'Fluffy Alpaca', rarity: 'Epic', weight: 600, income: 15, svg: graphics.alpaca },
          { id: 'c5', name: 'Golden Goose', rarity: 'Legendary', weight: 290, income: 50, svg: graphics.goose },
          { id: 'c6', name: 'Celestial Pegasus', rarity: 'Mythical', weight: 100, income: 200, svg: graphics.mythical_starter },
          { id: 'c7', name: 'Rainbow Pegasus', rarity: 'Exotic', weight: 10, income: 1000, svg: graphics.pegasus }
        ]
      },
      egg2: {
        title: '🌾 Grassland Egg',
        desc: 'Cost per egg: 2,500 Gold (Savanna & Carnivores)',
        cost: 2500,
        reqRebirths: 1,
        bossName: 'Eclipse Sovereign Lion',
        bossGraphic: graphics.boss2,
        graphic: eggGraphics.egg2,
        panelClass: 'panel-egg2',
        pool: [
          { id: 'c8', name: 'Swift Rabbit', rarity: 'Common', weight: 4500, income: 20, svg: graphics.rabbit },
          { id: 'c9', name: 'Striped Zebra', rarity: 'Uncommon', weight: 3000, income: 50, svg: graphics.zebra },
          { id: 'c10', name: 'Bouncy Kangaroo', rarity: 'Rare', weight: 1500, income: 120, svg: graphics.kangaroo },
          { id: 'c11', name: 'Sprinter Cheetah', rarity: 'Epic', weight: 600, income: 300, svg: graphics.cheetah },
          { id: 'c12', name: 'Savanna King Lion', rarity: 'Legendary', weight: 290, income: 800, svg: graphics.lion },
          { id: 'c13', name: 'Twilight White Tiger', rarity: 'Mythical', weight: 100, income: 2500, svg: graphics.mythical_grass },
          { id: 'c14', name: 'Neon Fantasy Lion', rarity: 'Exotic', weight: 10, income: 10000, svg: graphics.whitetiger }
        ]
      },
      egg3: {
        title: '🌊 Ocean Egg',
        desc: 'Cost per egg: 50,000 Gold (Marine Life)',
        cost: 50000,
        reqRebirths: 2,
        bossName: 'Abyssal Tide Megalodon',
        bossGraphic: graphics.boss3,
        graphic: eggGraphics.egg3,
        panelClass: 'panel-egg3',
        pool: [
          { id: 'c15', name: 'Little Fish', rarity: 'Common', weight: 4500, income: 150, svg: graphics.fish },
          { id: 'c16', name: 'Playful Dolphin', rarity: 'Uncommon', weight: 3000, income: 400, svg: graphics.dolphin },
          { id: 'c17', name: 'Giant Sea Turtle', rarity: 'Rare', weight: 1500, income: 1000, svg: graphics.seaturtle },
          { id: 'c18', name: 'Glowing Electric Octopus', rarity: 'Epic', weight: 600, income: 2500, svg: graphics.octopus },
          { id: 'c19', name: 'Deep Sea Shark', rarity: 'Legendary', weight: 290, income: 7000, svg: graphics.shark },
          { id: 'c20', name: 'Ancient Kraken', rarity: 'Mythical', weight: 100, income: 20000, svg: graphics.kraken },
          { id: 'c21', name: 'Abyssal Leviathan', rarity: 'Exotic', weight: 10, income: 80000, svg: graphics.leviathan }
        ]
      },
      egg4: {
        title: '❄️ Arctic Egg',
        desc: 'Cost per egg: 1,000,000 Gold (Polar Animals)',
        cost: 1000000,
        reqRebirths: 3,
        bossName: 'Frost Wyvern Drake',
        bossGraphic: graphics.boss4,
        graphic: eggGraphics.egg4,
        panelClass: 'panel-egg4',
        pool: [
          { id: 'c22', name: 'Baby Penguin', rarity: 'Common', weight: 4500, income: 1000, svg: graphics.penguin },
          { id: 'c23', name: 'Baby Seal', rarity: 'Uncommon', weight: 3000, income: 3000, svg: graphics.seal },
          { id: 'c24', name: 'Fluffy Polar Bear', rarity: 'Rare', weight: 1500, income: 8000, svg: graphics.polarbear },
          { id: 'c25', name: 'Aurora Fox', rarity: 'Epic', weight: 600, income: 20000, svg: graphics.aurorafox },
          { id: 'c26', name: 'Giant Yeti', rarity: 'Legendary', weight: 290, income: 60000, svg: graphics.yeti },
          { id: 'c27', name: 'Absolute Frost God', rarity: 'Mythical', weight: 100, income: 200000, svg: graphics.mythical_arctic },
          { id: 'c28', name: 'Frost Dragon', rarity: 'Exotic', weight: 10, income: 1000000, svg: graphics.frostdragon }
        ]
      },
      egg5: {
        title: '🔥 Volcano Egg',
        desc: 'Cost per egg: 20,000,000 Gold (Magma Creatures)',
        cost: 20000000,
        reqRebirths: 4,
        bossName: 'Lava Titan Turtle',
        bossGraphic: graphics.boss5,
        graphic: eggGraphics.egg5,
        panelClass: 'panel-egg5',
        pool: [
          { id: 'c29', name: 'Little Lava Lizard', rarity: 'Common', weight: 4500, income: 8000, svg: graphics.lavalizard },
          { id: 'c30', name: 'Flame Sprite', rarity: 'Uncommon', weight: 3000, income: 25000, svg: graphics.flamesprite },
          { id: 'c31', name: 'Magma Turtle', rarity: 'Rare', weight: 1500, income: 70000, svg: graphics.magmaturtle },
          { id: 'c32', name: 'Phoenix', rarity: 'Epic', weight: 600, income: 180000, svg: graphics.phoenix },
          { id: 'c33', name: 'Magma Dragon', rarity: 'Legendary', weight: 290, income: 500000, svg: graphics.magmadragon },
          { id: 'c34', name: 'Doomsday Dragon Zargan', rarity: 'Mythical', weight: 100, income: 1500000, svg: graphics.mythical_volcano },
          { id: 'c35', name: 'Infernal Ifrit', rarity: 'Exotic', weight: 10, income: 8000000, svg: graphics.ifrit }
        ]
      },
      egg6: {
        title: '🌌 Cosmos Egg',
        desc: 'Cost per egg: 500,000,000 Gold (Galactic Ultimate)',
        cost: 500000000,
        reqRebirths: 5,
        bossName: 'Starlight Ether Leviathan',
        bossGraphic: graphics.boss6,
        graphic: eggGraphics.egg6,
        panelClass: 'panel-egg6',
        pool: [
          { id: 'c36', name: 'Starlight Jelly', rarity: 'Common', weight: 4500, income: 60000, svg: graphics.stargelly },
          { id: 'c37', name: 'Little Alien', rarity: 'Uncommon', weight: 3000, income: 200000, svg: graphics.alien },
          { id: 'c38', name: 'Meteor Lion', rarity: 'Rare', weight: 1500, income: 600000, svg: graphics.meteorsnipe },
          { id: 'c39', name: 'Nebula Pegasus', rarity: 'Epic', weight: 600, income: 1500000, svg: graphics.nebulapegasus },
          { id: 'c40', name: 'Black Hole Kraken', rarity: 'Legendary', weight: 290, income: 4500500, svg: graphics.blackholekraken },
          { id: 'c41', name: 'Dimension Singularity', rarity: 'Mythical', weight: 100, income: 12000000, svg: graphics.mythical_cosmos },
          { id: 'c42', name: 'Cosmic Leviathan', rarity: 'Exotic', weight: 10, income: 60000000, svg: graphics.cosmicleviathan }
        ]
      }
    };

    let allCreatures = [];
    Object.keys(eggs).forEach(eggKey => {
      const egg = eggs[eggKey];
      const totalWeight = egg.pool.reduce((acc, cur) => acc + cur.weight, 0);
      egg.pool.forEach(c => {
        c.percentage = ((c.weight / totalWeight) * 100).toFixed(1);
        allCreatures.push(c);
      });
    });

    function init() {
      const collectionEl = document.getElementById('collection-list');
      collectionEl.innerHTML = '';
      
      allCreatures.forEach(c => {
        state.unlockedCreatures[c.id] = 0;
        
        const card = document.createElement('div');
        card.id = `collection-${c.id}`;
        card.className = `collection-item rarity-${c.rarity} locked`;
        card.innerHTML = `
          <span class="count-badge" id="count-${c.id}">x0</span>
          ${c.svg}
          <strong style="margin-top:2px; font-size:10px;">${c.name}</strong>
          <span style="font-size:9px; opacity:0.8;">${c.rarity}</span>
          <span style="font-size:9px; color:#f9e2af; margin-top:1px;">+${c.income.toLocaleString()}/s</span>
          <span style="font-size:8px; color:#a6adc8; opacity:0.7;">${c.percentage}%</span>
        `;
        collectionEl.appendChild(card);
      });

      renderCurrentEgg();
      setInterval(generateGold, 1000);
      updateUI();
    }

    function selectEgg(eggKey) {
      if (isHatching) return;
      if (isAutoHatching) toggleAutoHatch();

      state.selectedEggKey = eggKey;

      document.querySelectorAll('.tab-btn').forEach(btn => btn.classList.remove('active'));
      document.getElementById(`tab-${eggKey}`).classList.add('active');

      renderCurrentEgg();
      updateUI();
    }

    function renderThemeEffects(eggKey) {
      const panelEl = document.getElementById('egg-display-panel');
      panelEl.className = `egg-display-panel ${eggs[eggKey].panelClass}`;

      const fxLayer = document.getElementById('theme-fx-layer');
      fxLayer.innerHTML = '';

      if (eggKey === 'egg1') {
        for (let i = 0; i < 6; i++) {
          const star = document.createElement('div');
          star.className = 'fx-star';
          star.style.width = `${Math.random() * 6 + 4}px`;
          star.style.height = star.style.width;
          star.style.left = `${Math.random() * 100}%`;
          star.style.top = `${Math.random() * 100}%`;
          fxLayer.appendChild(star);
        }
      } else if (eggKey === 'egg2') {
        for (let i = 0; i < 7; i++) {
          const leaf = document.createElement('div');
          leaf.className = 'fx-leaf';
          leaf.style.width = `${Math.random() * 10 + 8}px`;
          leaf.style.height = `${Math.random() * 6 + 4}px`;
          leaf.style.left = `${Math.random() * 80}%`;
          fxLayer.appendChild(leaf);
        }
      } else if (eggKey === 'egg3') {
        const coralBox = document.createElement('div');
        coralBox.className = 'fx-coral';
        coralBox.innerHTML = `<div class="coral-item">🌿</div><div class="coral-item">🪸</div><div class="coral-item">🌿</div>`;
        fxLayer.appendChild(coralBox);
      } else if (eggKey === 'egg4') {
        for (let i = 0; i < 15; i++) {
          const snow = document.createElement('div');
          snow.className = 'fx-snowflake';
          snow.style.width = `${Math.random() * 5 + 3}px`;
          snow.style.height = snow.style.width;
          snow.style.left = `${Math.random() * 100}%`;
          fxLayer.appendChild(snow);
        }
      } else if (eggKey === 'egg5') {
        for (let i = 0; i < 8; i++) {
          const bubble = document.createElement('div');
          bubble.className = 'fx-lava-bubble';
          bubble.style.width = `${Math.random() * 10 + 6}px`;
          bubble.style.height = bubble.style.width;
          bubble.style.left = `${Math.random() * 90}%`;
          fxLayer.appendChild(bubble);
        }
      } else if (eggKey === 'egg6') {
        for (let i = 0; i < 12; i++) {
          const star = document.createElement('div');
          star.className = 'fx-star';
          star.style.width = `${Math.random() * 5 + 3}px`;
          star.style.height = star.style.width;
          star.style.left = `${Math.random() * 100}%`;
          star.style.top = `${Math.random() * 100}%`;
          fxLayer.appendChild(star);
        }
      }
    }

    function renderCurrentEgg() {
      const currentEgg = eggs[state.selectedEggKey];
      document.getElementById('egg-title').innerText = currentEgg.title;
      document.getElementById('egg-cost-info').innerText = currentEgg.desc;
      document.getElementById('huge-egg-svg').innerHTML = currentEgg.graphic.svg;
      
      const effectRing = document.getElementById('egg-effect-ring');
      effectRing.className = `egg-effect-ring ${currentEgg.graphic.effectClass}`;

      renderThemeEffects(state.selectedEggKey);

      const dropListEl = document.getElementById('egg-drop-list');
      dropListEl.innerHTML = '';
      currentEgg.pool.forEach(c => {
        const row = document.createElement('div');
        row.className = `drop-item-row rarity-${c.rarity}`;
        row.innerHTML = `<span class="drop-item-name">• ${c.name}</span><span style="font-weight:bold;">${c.percentage}%</span>`;
        dropListEl.appendChild(row);
      });

      const bossBtn = document.getElementById('btn-boss');
      if (state.bossCleared[state.selectedEggKey]) {
        bossBtn.innerText = `👑 ${currentEgg.bossName} Cleared`;
      } else {
        bossBtn.innerText = `⚔️ Challenge ${currentEgg.bossName}`;
      }
    }

    function stopBossCanvas() {
      if (activeCanvasAnimation) {
        cancelAnimationFrame(activeCanvasAnimation);
        activeCanvasAnimation = null;
      }
      document.getElementById('boss-battle-overlay').classList.remove('earthquake-shake');
    }

    function surrenderBossBattle() {
      if (activeClockInterval) clearInterval(activeClockInterval);
      if (activeBattleInterval) clearInterval(activeBattleInterval);
      stopBossCanvas();
      document.getElementById('boss-battle-overlay').classList.remove('active');
      log(`🏳️ <b>[Surrender]</b> Retreated from the battle.`);
    }

    /* ==========================================================================
       [보스전 Canvas 초고퀄리티 파티클/그래픽 애니메이션 엔진]
       ========================================================================== */
    function initBossCanvasAnimation(eggKey) {
      stopBossCanvas();

      const overlay = document.getElementById('boss-battle-overlay');
      const canvas = document.getElementById('boss-canvas');
      const ctx = canvas.getContext('2d');

      let width = canvas.width = window.innerWidth;
      let height = canvas.height = window.innerHeight;

      const handleResize = () => {
        width = canvas.width = window.innerWidth;
        height = canvas.height = window.innerHeight;
      };
      window.addEventListener('resize', handleResize);

      let frame = 0;
      let particles = [];

      // 1. 골렘: 파쇄 암석 파티클 생성
      if (eggKey === 'egg1') {
        overlay.classList.add('earthquake-shake');
        for (let i = 0; i < 40; i++) {
          particles.push({
            x: Math.random() * width,
            y: height + Math.random() * 100,
            size: Math.random() * 18 + 6,
            vy: -(Math.random() * 7 + 3),
            vx: (Math.random() - 0.5) * 4,
            rotation: Math.random() * Math.PI * 2,
            vr: (Math.random() - 0.5) * 0.1,
            color: Math.random() > 0.5 ? '#27ae60' : '#34495e'
          });
        }
      } 
      // 2. 라이언: 초승달빛 가루 파티클
      else if (eggKey === 'egg2') {
        for (let i = 0; i < 60; i++) {
          particles.push({
            x: Math.random() * width,
            y: Math.random() * height,
            r: Math.random() * 4 + 1.5,
            alpha: Math.random() * 0.8 + 0.2,
            vy: -(Math.random() * 0.8 + 0.2),
            vx: (Math.random() - 0.5) * 0.6,
            color: Math.random() > 0.4 ? '#f1c40f' : '#cba6f7'
          });
        }
      } 
      // 3. 메갈로돈: 실제 오션 수중 물보라 파티클
      else if (eggKey === 'egg3') {
        for (let i = 0; i < 80; i++) {
          particles.push({
            x: Math.random() * width,
            y: height - Math.random() * 200,
            r: Math.random() * 4 + 1,
            vy: -(Math.random() * 3 + 1),
            vx: (Math.random() - 0.5) * 2,
            alpha: Math.random() * 0.7 + 0.3
          });
        }
      } 
      // 4. 서리 드래곤: 강풍 3D 눈보라 파티클
      else if (eggKey === 'egg4') {
        for (let i = 0; i < 150; i++) {
          particles.push({
            x: Math.random() * width * 1.5 - width * 0.25,
            y: Math.random() * height - height,
            size: Math.random() * 5 + 1.5,
            vx: (Math.random() * 12 + 8),
            vy: (Math.random() * 10 + 6),
            alpha: Math.random() * 0.8 + 0.2
          });
        }
      } 
      // 5. 라바 거북이: 화산 분출 마그마 파티클
      else if (eggKey === 'egg5') {
        for (let i = 0; i < 100; i++) {
          particles.push({
            x: width * 0.5 + (Math.random() - 0.5) * 80,
            y: height * 0.65,
            vx: (Math.random() - 0.5) * 14,
            vy: -(Math.random() * 16 + 8),
            gravity: 0.3,
            size: Math.random() * 6 + 2,
            color: Math.random() > 0.3 ? '#ff3838' : '#facc15',
            life: Math.random() * 60 + 40
          });
        }
      } 
      // 6. 코스믹 레비아단: 대규모 은하계 성간 파티클 & 블랙홀 중력 흡수 입자
      else if (eggKey === 'egg6') {
        for (let i = 0; i < 350; i++) {
          let dist = Math.random() * (Math.max(width, height) * 0.7) + 30;
          let angle = Math.random() * Math.PI * 2;
          particles.push({
            dist: dist,
            angle: angle,
            speed: (1 / (dist + 50)) * 4.5 + 0.003,
            size: Math.random() * 3.5 + 0.8,
            color: ['#cba6f7', '#89b4fa', '#ff7675', '#f9e2af', '#38bdf8', '#ff007f'][Math.floor(Math.random() * 6)]
          });
        }
      }

      function animate() {
        ctx.clearRect(0, 0, width, height);
        frame++;

        // ==================== [1. 🌱 골렘] ====================
        if (eggKey === 'egg1') {
          let bgGrad = ctx.createLinearGradient(0, 0, 0, height);
          bgGrad.addColorStop(0, '#06130b');
          bgGrad.addColorStop(0.6, '#0f2d1a');
          bgGrad.addColorStop(1, '#1b4d2e');
          ctx.fillStyle = bgGrad;
          ctx.fillRect(0, 0, width, height);

          particles.forEach(p => {
            p.y += p.vy;
            p.x += p.vx;
            p.rotation += p.vr;
            if (p.y < -50) {
              p.y = height + 50;
              p.x = Math.random() * width;
            }

            ctx.save();
            ctx.translate(p.x, p.y);
            ctx.rotate(p.rotation);
            ctx.fillStyle = p.color;
            ctx.fillRect(-p.size / 2, -p.size / 2, p.size, p.size);
            ctx.restore();
          });

          ctx.strokeStyle = 'rgba(74, 222, 128, 0.25)';
          ctx.lineWidth = 3;
          ctx.beginPath();
          let lineY = height * 0.7 + Math.sin(frame * 0.2) * 10;
          ctx.moveTo(0, lineY);
          for (let x = 0; x < width; x += 40) {
            ctx.lineTo(x, lineY + (Math.random() - 0.5) * 30);
          }
          ctx.stroke();
        }

        // ==================== [2. 🌾 라이언 - 영롱한 초승달] ====================
        else if (eggKey === 'egg2') {
          let bgGrad = ctx.createRadialGradient(width * 0.5, height * 0.3, 50, width * 0.5, height * 0.5, width);
          bgGrad.addColorStop(0, '#2d1836');
          bgGrad.addColorStop(0.5, '#190e24');
          bgGrad.addColorStop(1, '#08040c');
          ctx.fillStyle = bgGrad;
          ctx.fillRect(0, 0, width, height);

          // 🌙 초승달(Crescent Moon) 연출
          let moonX = width * 0.5;
          let moonY = height * 0.26;
          let moonRadius = Math.min(width, height) * 0.15;

          // 초승달 은은한 펄스 Glow
          let glowPulse = Math.sin(frame * 0.03) * 15;
          let moonGlow = ctx.createRadialGradient(moonX, moonY, moonRadius * 0.5, moonX, moonY, moonRadius + 90 + glowPulse);
          moonGlow.addColorStop(0, 'rgba(254, 240, 138, 0.85)');
          moonGlow.addColorStop(0.5, 'rgba(192, 132, 252, 0.25)');
          moonGlow.addColorStop(1, 'transparent');
          ctx.fillStyle = moonGlow;
          ctx.beginPath();
          ctx.arc(moonX, moonY, moonRadius + 100, 0, Math.PI * 2);
          ctx.fill();

          // 초승달 본체 (원 2개를 겹쳐서 초승달 모양 깎아내기)
          ctx.save();
          let moonBody = ctx.createLinearGradient(moonX - moonRadius, moonY - moonRadius, moonX + moonRadius, moonY + moonRadius);
          moonBody.addColorStop(0, '#ffffff');
          moonBody.addColorStop(0.5, '#fef08a');
          moonBody.addColorStop(1, '#e67e22');
          
          ctx.fillStyle = moonBody;
          ctx.beginPath();
          ctx.arc(moonX, moonY, moonRadius, 0, Math.PI * 2);
          ctx.fill();

          // 안쪽을 어두운 원으로 파내어 초승달 모양 만들기
          ctx.globalCompositeOperation = 'destination-out';
          ctx.beginPath();
          ctx.arc(moonX + moonRadius * 0.45, moonY - moonRadius * 0.15, moonRadius * 0.85, 0, Math.PI * 2);
          ctx.fill();
          ctx.restore();

          // 달빛 입자
          particles.forEach(p => {
            p.y += p.vy;
            p.x += p.vx;
            if (p.y < 0) p.y = height;
            ctx.fillStyle = p.color;
            ctx.globalAlpha = p.alpha * (0.6 + Math.sin(frame * 0.05 + p.x) * 0.4);
            ctx.beginPath();
            ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
            ctx.fill();
            ctx.globalAlpha = 1.0;
          });
        }

        // ==================== [3. 🌊 메갈로돈] ====================
        else if (eggKey === 'egg3') {
          let bgGrad = ctx.createLinearGradient(0, 0, 0, height);
          bgGrad.addColorStop(0, '#041326');
          bgGrad.addColorStop(0.6, '#06203d');
          bgGrad.addColorStop(1, '#020b17');
          ctx.fillStyle = bgGrad;
          ctx.fillRect(0, 0, width, height);

          const drawWave = (offsetY, amp, freq, speed, color) => {
            ctx.fillStyle = color;
            ctx.beginPath();
            ctx.moveTo(0, height);
            for (let x = 0; x <= width; x += 10) {
              let y = height * offsetY + Math.sin(x * freq + frame * speed) * amp + Math.cos(x * 0.005 + frame * 0.02) * (amp * 0.5);
              ctx.lineTo(x, y);
            }
            ctx.lineTo(width, height);
            ctx.closePath();
            ctx.fill();
          };

          drawWave(0.45, 30, 0.008, 0.03, 'rgba(12, 74, 110, 0.6)');
          drawWave(0.52, 25, 0.012, -0.04, 'rgba(3, 105, 161, 0.7)');
          drawWave(0.60, 35, 0.006, 0.05, 'rgba(56, 189, 248, 0.85)');

          particles.forEach(p => {
            p.y += p.vy;
            p.x += p.vx;
            if (p.y < height * 0.4) {
              p.y = height - Math.random() * 100;
              p.x = Math.random() * width;
            }
            ctx.fillStyle = '#bae6fd';
            ctx.globalAlpha = p.alpha;
            ctx.beginPath();
            ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
            ctx.fill();
            ctx.globalAlpha = 1.0;
          });
        }

        // ==================== [4. ❄️ 서리 드래곤] ====================
        else if (eggKey === 'egg4') {
          let bgGrad = ctx.createLinearGradient(0, 0, width, height);
          bgGrad.addColorStop(0, '#0c2340');
          bgGrad.addColorStop(1, '#030a14');
          ctx.fillStyle = bgGrad;
          ctx.fillRect(0, 0, width, height);

          ctx.fillStyle = '#ffffff';
          particles.forEach(p => {
            p.x += p.vx;
            p.y += p.vy;

            if (p.x > width || p.y > height) {
              p.x = Math.random() * width * 1.5 - width * 0.5;
              p.y = -20;
            }

            ctx.globalAlpha = p.alpha;
            ctx.beginPath();
            ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
            ctx.fill();

            ctx.strokeStyle = 'rgba(224, 242, 254, 0.4)';
            ctx.lineWidth = p.size * 0.8;
            ctx.beginPath();
            ctx.moveTo(p.x, p.y);
            ctx.lineTo(p.x - p.vx * 1.5, p.y - p.vy * 1.5);
            ctx.stroke();
            ctx.globalAlpha = 1.0;
          });
        }

        // ==================== [5. 🔥 라바 거북이] ====================
        else if (eggKey === 'egg5') {
          let bgGrad = ctx.createLinearGradient(0, 0, 0, height);
          bgGrad.addColorStop(0, '#2a0808');
          bgGrad.addColorStop(0.5, '#4a0e0e');
          bgGrad.addColorStop(1, '#110303');
          ctx.fillStyle = bgGrad;
          ctx.fillRect(0, 0, width, height);

          let vX = width * 0.5;
          let vY = height * 0.72;
          ctx.fillStyle = '#1c0a0a';
          ctx.beginPath();
          ctx.moveTo(vX - 280, height);
          ctx.lineTo(vX - 60, vY);
          ctx.lineTo(vX + 60, vY);
          ctx.lineTo(vX + 280, height);
          ctx.closePath();
          ctx.fill();

          let craterGlow = ctx.createRadialGradient(vX, vY, 10, vX, vY, 90);
          craterGlow.addColorStop(0, '#fef08a');
          craterGlow.addColorStop(0.4, '#f97316');
          craterGlow.addColorStop(1, 'transparent');
          ctx.fillStyle = craterGlow;
          ctx.beginPath();
          ctx.arc(vX, vY, 90, 0, Math.PI * 2);
          ctx.fill();

          particles.forEach(p => {
            p.vy += p.gravity;
            p.x += p.vx;
            p.y += p.vy;
            p.life--;

            if (p.life <= 0 || p.y > height) {
              p.x = vX + (Math.random() - 0.5) * 60;
              p.y = vY;
              p.vx = (Math.random() - 0.5) * 16;
              p.vy = -(Math.random() * 18 + 8);
              p.life = Math.random() * 60 + 40;
            }

            ctx.fillStyle = p.color;
            ctx.beginPath();
            ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
            ctx.fill();
          });
        }

        // ==================== [6. 🌌 코스믹 레비아단 - 초대형 은하계 & 고퀄리티 블랙홀] ====================
        else if (eggKey === 'egg6') {
          // 광활한 딥 우주 배경
          ctx.fillStyle = '#020106';
          ctx.fillRect(0, 0, width, height);

          let centerX = width * 0.5;
          let centerY = height * 0.45;

          // 🌀 초대형 회전 은하계 성간 파티클 필드
          particles.forEach(p => {
            p.angle += p.speed;
            // 블랙홀 쪽으로 살짝 빨려 들어가는 나선형 회전 궤적
            p.dist -= 0.15;
            if (p.dist < 40) p.dist = Math.max(width, height) * 0.7;

            let x = centerX + Math.cos(p.angle) * p.dist;
            let y = centerY + Math.sin(p.angle) * (p.dist * 0.55); // 입체적 타원 은하 궤도

            ctx.fillStyle = p.color;
            ctx.beginPath();
            ctx.arc(x, y, p.size, 0, Math.PI * 2);
            ctx.fill();
          });

          // 🕳️ 초고퀄리티 블랙홀 & 강착원반(Accretion Disk) 연출
          let bhRadius = 55;

          // 외곽 가스 광채 레이어
          let outerGlow = ctx.createRadialGradient(centerX, centerY, bhRadius, centerX, centerY, bhRadius * 3.5);
          outerGlow.addColorStop(0, 'rgba(168, 85, 247, 0.4)');
          outerGlow.addColorStop(0.5, 'rgba(56, 189, 248, 0.2)');
          outerGlow.addColorStop(1, 'transparent');
          ctx.fillStyle = outerGlow;
          ctx.beginPath();
          ctx.arc(centerX, centerY, bhRadius * 3.5, 0, Math.PI * 2);
          ctx.fill();

          // 빛이 휘어지는 강착원반 (Accretion Disk) - 타원형 회전
          let ringGrad = ctx.createRadialGradient(centerX, centerY, bhRadius * 0.9, centerX, centerY, bhRadius * 2.5);
          ringGrad.addColorStop(0, '#ffffff');
          ringGrad.addColorStop(0.2, '#f43f5e');
          ringGrad.addColorStop(0.5, '#a855f7');
          ringGrad.addColorStop(0.8, '#38bdf8');
          ringGrad.addColorStop(1, 'transparent');

          ctx.save();
          ctx.translate(centerX, centerY);
          ctx.scale(1, 0.38); // 3D 기울임 각도
          ctx.rotate(frame * 0.015); // 원반 회전 모션
          ctx.fillStyle = ringGrad;
          ctx.beginPath();
          ctx.arc(0, 0, bhRadius * 2.5, 0, Math.PI * 2);
          ctx.fill();
          ctx.restore();

          // 블랙홀 사건의 지평선 (Event Horizon - 완벽한 암흑 코어)
          let bhCore = ctx.createRadialGradient(centerX, centerY, 2, centerX, centerY, bhRadius);
          bhCore.addColorStop(0, '#000000');
          bhCore.addColorStop(0.8, '#000000');
          bhCore.addColorStop(0.95, '#1e1b4b');
          bhCore.addColorStop(1, '#c084fc');

          ctx.fillStyle = bhCore;
          ctx.beginPath();
          ctx.arc(centerX, centerY, bhRadius, 0, Math.PI * 2);
          ctx.fill();
        }

        activeCanvasAnimation = requestAnimationFrame(animate);
      }

      animate();
    }

    function startBossBattle() {
      const eggKey = state.selectedEggKey;
      const egg = eggs[eggKey];

      let nonExoticSum = 0;
      egg.pool.forEach(c => { if (c.rarity !== 'Exotic') nonExoticSum += c.income; });

      let bossMaxHp = (nonExoticSum * state.multiplier) * 60;
      let currentBossHp = bossMaxHp;

      const overlay = document.getElementById('boss-battle-overlay');
      const title = document.getElementById('boss-battle-title');
      const bossIcon = document.getElementById('boss-fighter-icon');
      const playerIcon = document.getElementById('player-fighter');
      const beamEl = document.getElementById('attack-beam');
      const arena = document.getElementById('battle-arena');
      const hpBar = document.getElementById('boss-hp-bar');
      const hpText = document.getElementById('boss-hp-text');
      const timerText = document.getElementById('boss-timer-text');

      overlay.classList.add('active');
      initBossCanvasAnimation(eggKey);

      bossIcon.className = 'boss-fighter';
      title.innerText = `⚔️ ${egg.bossName} Appeared!`;
      bossIcon.innerHTML = egg.bossGraphic;

      let timeLeft = 60;
      timerText.innerText = `Time Left: 1:00`;
      let secCounter = 0;

      activeClockInterval = setInterval(() => {
        timeLeft--;
        let mins = Math.floor(timeLeft / 60);
        let secs = timeLeft % 60;
        timerText.innerText = `Time Left: ${mins}:${secs < 10 ? '0' : ''}${secs}`;

        if (timeLeft <= 0) {
          clearInterval(activeClockInterval);
          clearInterval(activeBattleInterval);
          stopBossCanvas();
          overlay.classList.remove('active');
          log(`❌ <b>[Boss Failed]</b> Time ran out.`);
        }
      }, 1000);

      activeBattleInterval = setInterval(() => {
        let currentCps = 0;
        allCreatures.forEach(c => { if (state.unlockedCreatures[c.id] > 0) currentCps += c.income; });
        currentCps *= state.multiplier;
        if (currentCps <= 0) currentCps = 0;

        let damagePerTick = currentCps / 10;
        currentBossHp -= damagePerTick;
        if (currentBossHp < 0) currentBossHp = 0;

        let hpPercent = (currentBossHp / bossMaxHp) * 100;
        hpBar.style.width = `${hpPercent}%`;
        hpText.innerText = `HP: ${Math.max(0, Math.floor(currentBossHp)).toLocaleString()} / ${Math.floor(bossMaxHp).toLocaleString()} (${Math.floor(hpPercent)}%)`;

        secCounter++;
        if (secCounter >= 10) {
          secCounter = 0;
          if (currentCps > 0) {
            playerIcon.classList.remove('attack-pulse');
            void playerIcon.offsetWidth; 
            playerIcon.classList.add('attack-pulse');

            beamEl.classList.remove('active');
            void beamEl.offsetWidth; 
            beamEl.classList.add('active');

            setTimeout(() => {
              bossIcon.classList.remove('hit-shake');
              void bossIcon.offsetWidth; 
              bossIcon.classList.add('hit-shake');

              const dmgFloat = document.createElement('div');
              dmgFloat.className = 'floating-damage';
              dmgFloat.innerText = `-${Math.floor(currentCps).toLocaleString()}`;
              dmgFloat.style.right = `${10 + Math.random() * 30}px`;
              dmgFloat.style.top = `${20 + Math.random() * 30}px`;
              arena.appendChild(dmgFloat);

              setTimeout(() => dmgFloat.remove(), 750);
            }, 150);
          }
        }

        if (currentBossHp <= 0) {
          clearInterval(activeClockInterval);
          clearInterval(activeBattleInterval);
          bossIcon.classList.add('boss-dead');

          setTimeout(() => {
            stopBossCanvas();
            overlay.classList.remove('active');
            state.bossCleared[eggKey] = true;
            let rewardGold = egg.cost * 150;
            state.gold += rewardGold;
            log(`🎉 <b>[Boss Victory!]</b> Defeated ${egg.bossName}! Reward: <b>${rewardGold.toLocaleString()} Gold</b>!`);
            renderCurrentEgg();
            updateUI();
          }, 800);
        }
      }, 100);
    }

    function executeHatchCinematic(count, onComplete) {
      const eggKey = state.selectedEggKey;
      const egg = eggs[eggKey];
      const totalCost = egg.cost * count;

      if (state.gold < totalCost) {
        log(`❌ Not enough gold! (Required: ${totalCost.toLocaleString()})`);
        if (onComplete) onComplete(false);
        return;
      }

      state.gold -= totalCost;
      isHatching = true;
      updateUI();

      const overlay = document.getElementById('cinematic-overlay');
      const area = document.getElementById('cinematic-area');
      const title = document.getElementById('cinematic-title');
      
      title.innerText = count === 1 ? `🥚 Shaking ${egg.title}...` : `🥚 Shaking ${count}x ${egg.title}...`;
      area.innerHTML = '';
      
      for (let i = 0; i < Math.min(count, 10); i++) {
        const div = document.createElement('div');
        div.className = 'floating-egg';
        div.innerHTML = egg.graphic.svg;
        area.appendChild(div);
      }
      if (count > 10) {
        const more = document.createElement('div');
        more.style.color = '#f9e2af';
        more.style.fontSize = '18px';
        more.innerText = `and ${count - 10} more...`;
        area.appendChild(more);
      }

      overlay.classList.add('active');

      setTimeout(() => {
        title.innerText = '✨ Creatures Born!';
        area.innerHTML = '';

        const totalWeight = egg.pool.reduce((acc, cur) => acc + cur.weight, 0);
        let sessionResults = {};
        let hatchedList = [];

        for (let i = 0; i < count; i++) {
          let randomNum = Math.random() * totalWeight;
          let selected = null;

          for (let creature of egg.pool) {
            if (randomNum < creature.weight) {
              selected = creature;
              break;
            }
            randomNum -= creature.weight;
          }

          state.unlockedCreatures[selected.id]++;
          sessionResults[selected.id] = (sessionResults[selected.id] || 0) + 1;
          hatchedList.push(selected);
        }

        hatchedList.slice(0, 8).forEach(c => {
          const div = document.createElement('div');
          div.className = `floating-creature rarity-${c.rarity}`;
          div.innerHTML = `${c.svg}<span style="font-size:10px; font-weight:bold;">${c.name}</span>`;
          area.appendChild(div);
        });

        egg.pool.forEach(c => {
          if (state.unlockedCreatures[c.id] > 0) {
            const cardEl = document.getElementById(`collection-${c.id}`);
            cardEl.classList.remove('locked');
            document.getElementById(`count-${c.id}`).innerText = `x${state.unlockedCreatures[c.id]}`;
          }
        });

        updateUI();

        setTimeout(() => {
          overlay.classList.remove('active');
          isHatching = false;
          if (onComplete) onComplete(true, sessionResults);
        }, 1100);

      }, 1100);
    }

    function hatchCurrentEgg(count) {
      if (isHatching || isAutoHatching) return;
      if (count >= 100 && state.reincarnations < 1) {
        log('❌ Bulk hatching requires at least 1 Rebirth!');
        return;
      }

      executeHatchCinematic(count, (success, results) => {
        if (success) {
          showModal(count, results);
          log(`🎉 Hatched ${count}x ${eggs[state.selectedEggKey].title}!`);
        }
      });
    }

    function toggleAutoHatch() {
      const autoBtn = document.getElementById('btn-auto');
      const egg = eggs[state.selectedEggKey];

      if (!isAutoHatching) {
        if (state.gold < egg.cost) {
          log(`❌ Not enough gold to start auto hatching!`);
          return;
        }
        isAutoHatching = true;
        autoBtn.classList.add('active');
        autoBtn.innerText = '⏹️ Stop Auto Hatching (ON)';
        log(`⚡ Started auto hatching for ${egg.title}.`);
        runAutoHatchStep();
      } else {
        isAutoHatching = false;
        autoBtn.classList.remove('active');
        autoBtn.innerText = '⚡ Start Auto Hatching';
        log(`⏹️ Auto hatching stopped.`);
        updateUI();
      }
    }

    function runAutoHatchStep() {
      if (!isAutoHatching) return;
      const currentEgg = eggs[state.selectedEggKey];

      if (state.gold < currentEgg.cost) {
        log(`❌ Out of gold. Auto hatching stopped.`);
        toggleAutoHatch();
        return;
      }

      executeHatchCinematic(1, (success) => {
        if (!success) { toggleAutoHatch(); return; }
        if (isAutoHatching) setTimeout(runAutoHatchStep, 300);
      });
    }

    function toggleCollectionModal(show) {
      const modal = document.getElementById('collection-modal');
      if (show) modal.classList.add('active');
      else modal.classList.remove('active');
    }

    function generateGold() {
      let baseIncomeSum = 0;
      allCreatures.forEach(c => { if (state.unlockedCreatures[c.id] > 0) baseIncomeSum += c.income; });

      const currentCps = baseIncomeSum * state.multiplier;
      state.gold += currentCps;

      document.getElementById('cps').innerText = Math.floor(currentCps).toLocaleString();
      updateUI();
    }

    function reincarnate() {
      const reqGold = 100000;
      if (state.gold < reqGold) {
        log(`❌ You need at least ${reqGold.toLocaleString()} Gold for Rebirth!`);
        return;
      }

      if (isAutoHatching) toggleAutoHatch();

      state.reincarnations++;
      state.multiplier = 1 + (state.reincarnations * 3.0);
      state.gold = 300;

      log(`🌀 <b>Rebirth Successful!</b> Count: ${state.reincarnations} (Multiplier: <b>${state.multiplier}x</b>)`);
      updateUI();
    }

    function updateUI() {
      document.getElementById('gold').innerText = Math.floor(state.gold).toLocaleString();
      document.getElementById('reincarnations').innerText = state.reincarnations;

      const hasRebirth1 = state.reincarnations >= 1;
      const hasRebirth2 = state.reincarnations >= 2;
      const hasRebirth3 = state.reincarnations >= 3;
      const hasRebirth4 = state.reincarnations >= 4;
      const hasRebirth5 = state.reincarnations >= 5;

      const tabEgg2 = document.getElementById('tab-egg2');
      const tabEgg3 = document.getElementById('tab-egg3');
      const tabEgg4 = document.getElementById('tab-egg4');
      const tabEgg5 = document.getElementById('tab-egg5');
      const tabEgg6 = document.getElementById('tab-egg6');

      if (hasRebirth1) { tabEgg2.disabled = false; tabEgg2.innerText = '🌾 Grassland Egg'; }
      if (hasRebirth2) { tabEgg3.disabled = false; tabEgg3.innerText = '🌊 Ocean Egg'; }
      if (hasRebirth3) { tabEgg4.disabled = false; tabEgg4.innerText = '❄️ Arctic Egg'; }
      if (hasReforth4 = hasRebirth4) { tabEgg5.disabled = false; tabEgg5.innerText = '🔥 Volcano Egg'; }
      if (hasRebirth5) { tabEgg6.disabled = false; tabEgg6.innerText = '🌌 Cosmos Egg'; }

      const currentEgg = eggs[state.selectedEggKey];
      document.getElementById('btn-hatch-1').disabled = isHatching || isAutoHatching || state.gold < currentEgg.cost;
      document.getElementById('btn-hatch-2').disabled = isHatching || isAutoHatching || state.gold < currentEgg.cost * 10;
      document.getElementById('btn-hatch-5').disabled = isHatching || isAutoHatching || state.gold < currentEgg.cost * 100 || !hasRebirth1;
      
      const btn1000 = document.getElementById('btn-hatch-10');
      btn1000.disabled = isHatching || isAutoHatching || state.gold < currentEgg.cost * 1000 || !hasRebirth1;
      btn1000.innerText = hasRebirth1 ? 'Hatch 1K🔥' : 'Hatch 1K🔒';

      const autoBtn = document.getElementById('btn-auto');
      if (!isAutoHatching) autoBtn.disabled = state.gold < currentEgg.cost;
    }

    function showModal(count, results) {
      const modal = document.getElementById('hatch-modal');
      const resultsContainer = document.getElementById('modal-results');
      document.getElementById('modal-title').innerText = count === 1 ? `✨ Hatch Results` : `✨ Hatch Results (${count}x)`;
      
      resultsContainer.innerHTML = '';
      Object.keys(results).forEach(id => {
        const creature = allCreatures.find(c => c.id === id);
        const qty = results[id];
        
        const row = document.createElement('div');
        row.className = `modal-result-row rarity-${creature.rarity}`;
        row.innerHTML = `<span><b>${creature.name}</b> <span style="font-size:11px; opacity:0.8;">[${creature.rarity}]</span></span><span style="font-weight:bold; color:#f9e2af;">+${qty}</span>`;
        resultsContainer.appendChild(row);
      });

      modal.classList.add('active');
    }

    function closeModal() { document.getElementById('hatch-modal').classList.remove('active'); }

    let logBox = document.getElementById('log');
    function log(message) {
      const newLog = document.createElement('div');
      newLog.innerHTML = message;
      logBox.appendChild(newLog);
      logBox.scrollTop = logBox.scrollHeight;
    }

    init();
  </script>
</body>
</html>
