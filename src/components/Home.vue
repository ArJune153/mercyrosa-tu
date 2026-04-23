<template>
  <div class="container-home">
    <img class="img-logo" :src="require('@/assets/mercy-logo-f.png')" alt="Background Image"/>
    <div class="button-container">
    <a href="https://lin.ee/knMX628" class="custom-button1">
        <i class="fas fa-user-plus"></i>  <!-- ไอคอนสมัครสมาชิก -->
        สมัครสมาชิก
    </a>
    <a href="https://lin.ee/knMX628" class="custom-button2">
        <i class="fas fa-comments"></i>  <!-- ไอคอนติดต่อแอดมิน -->
        ติดต่อแอดมิน
    </a>
</div>

    <div class="online-all">
  <div class="user-online-status">
    <i class="fas fa-circle online-icon"></i>
    <span class="online-count">ออนไลน์ <span class="online-num" ref="onlineCountAll">{{ onlineCountAll }}</span> คน</span>
  </div>
  </div>
  </div>
</template>

<script>
export default {
  name: "StatsCards",
  data() {
    return {
      currentIndex: 0,
      onlineCount1: "33,563",
      onlineCount2: "23,123",
      onlineCount3: "15,900",
      onlineCount4: "18,351",
      onlineCount5: "9874",
      onlineCount6: "13,254",
      onlineCountAll: "189,631",
      slides: [
        { src: 'certi.jpg', alt: 'Image 3' },
        { src: 'photo_6228624588875613744_y.jpg', alt: 'Image 1' },
        { src: 'photo_6228624588875613745_y.jpg', alt: 'Image 2' },      
      ],
      topUsersData : [
      { userName: "rosaa01xx", amount: "150,000", timestamp: "31 ส.ค. 2568" },
      { userName: "rosab89xx", amount: "130,500", timestamp: "31 ส.ค. 2568" },
      { userName: "rosae11xx", amount: "95,200", timestamp: "31 ส.ค. 2568" },
      { userName: "rosad04xx", amount: "83,000", timestamp: "31 ส.ค. 2568" },
      { userName: "rosae87xx", amount: "82,000", timestamp: "31 ส.ค. 2568" },
      { userName: "rosae35xx", amount: "78,000", timestamp: "31 ส.ค. 2568" },
    ],
    reviews : [
      { user: "rosaj23xx", text: "เว็บนี้ใช้งานง่าย ถอนเงินไวมาก", img: "photo-2568-06-02-13-24-49.jpg" },
      { user: "rosas16xx", text: "แตกหนักจนแฟนงง ว่าไปเอาเงินมาจากไหน", img: "photo-2568-06-21-13-38-31.jpg" },
      { user: "rosae56xx", text: "ระบบดี ไม่มีสะดุดเลย", img: "photo-2568-06-02-13-11-47.jpg" },
      { user: "rosax88xx", text: "โปรโมชั่นคุ้มสุด ๆ เลยครับ", img: "503804955-122126012606831043-7044484449309087338-n.jpg" },
      { user: "rosao16xx", text: "เล่นง่าย ได้เงินจริง", img: "490506081-122124348278773654-1591748651281217225-n.jpg" },
      { user: "rosad41xx", text: "แตกจริง! ไม่ต้องลุ้นเลย เงินเข้าไวสุด ๆ 💸", img: "533961598_1465905681078900_8473607776528464666_n.jpg" },
      { user: "rosad41xx", text: "จากหลักร้อยเป็นหลักหมื่นในคืนเดียว ว้าว!", img: "464195162_2477566235772141_6809220135929060331_n.jpg" },
      { user: "rosab71xx", text: "รองรับ TrueWallet ด้วย สะดวกมาก", img: "504143319_2219977065123389_83092695142278008_n.jpg" },
      { user: "rosat94xx", text: "แนะนำเพื่อน ได้โบนัสด้วย", img: "492242625_668943662417215_4482917277835435921_n.jpg" },
      { user: "rosal68xx", text: "ดีตรงที่มีภาษาไทยครบถ้วน", img: "518366934_736143816025493_1299983234092703859_n.jpg" },
      { user: "rosat28xx", text: "ฝากปุ๊บเงินเข้าปั๊บ", img: "533084719_1116500603710911_5818853113959217185_n.jpg" },
      { user: "rosao71xx", text: "แทบจะถอนทุกวัน ดีจริงๆเว็บนี้!", img: "277169807-3163265690584017-8353788208641286173-n.jpg" },
      { user: "rosaj88xx", text: "ชอบมีไลฟ์สดบอลให้ดูฟรี", img: "432694438-933306371801755-6605376483802637949-n.jpg" },
      { user: "rosaq38xx", text: "ทีมซัพพอร์ตดูแลดีมาก", img: "444482004_7798764536813604_3664008989486408448_n.md.jpg" },
      { user: "rosaz65xx", text: "อัตราต่อรองแฟร์สุด ๆ", img: "499992981-543532548818863-8863283426458467040-n.jpg" },
      { user: "rosaf86xx", text: "ถอนวันละพันทุกวัน แทบไม่ต้องทำงาน", img: "503202164-2075152429640793-785701917046162087-n.jpg" },
    ],
    rwindex:0
    };
  },
  methods: {
    createRankingCard(user, rank) {
        const rankingContainer = document.getElementById("rankingContainer");

        const card = document.createElement("div");
        card.classList.add("ranking-card");

        const speedClasses = ['fast-wave', 'medium-wave', 'slow-wave'];
        const selectedSpeedClass = speedClasses[Math.floor(Math.random() * speedClasses.length)];
        card.classList.add(selectedSpeedClass);

        // --- สร้างวันที่ปัจจุบันเป็นภาษาไทย พร้อมเลข 0 ข้างหน้า ---
        const now = new Date();
        const day = now.getDate().toString().padStart(2, '0'); // ใส่ 0 ถ้าวัน < 10
        const month = now.toLocaleDateString('th-TH', { month: 'short' });
        const year = now.getFullYear() + 543; // แปลงเป็น พ.ศ.
        const thaiDate = `${day} ${month} ${year}`;

        card.innerHTML = `
          <div class="card-details">
            <div class="info-section">
              <div class="user-name">ยูส: ${user.userName}</div>
              <div class="user-transaction">ยอดถอน: <span class="amount">${user.amount}</span></div>
              <div class="user-transaction">เวลา: ${thaiDate}</div>
            </div>
          </div>
          <div class="rank-info" data-rank="${rank}">
            <!-- จะแสดงหมายเลขอันดับที่นี่ -->
          </div>
        `;

        rankingContainer.appendChild(card);

        if (rankingContainer.children.length > 6) {
          rankingContainer.removeChild(rankingContainer.firstElementChild);
        }
      },
     animateNumber(refName, startValue, endValue, callback) {
      let currentValue = startValue;
      const step = Math.max(1, Math.ceil((endValue - startValue) / 20));

      // ใช้ Vue.nextTick เพื่อให้มั่นใจว่า DOM ถูกเรนเดอร์แล้ว
      this.$nextTick(() => {
        const element = this.$refs[refName];

        if (element) {
          const interval = setInterval(() => {
            currentValue += step;
            if (currentValue >= endValue) {
              clearInterval(interval);
              currentValue = endValue;
              if (callback) callback();
            }
            element.textContent = currentValue.toLocaleString();
          }, 100);
        }
      });
    },
    updateOnlineCount() {
      setInterval(() => {
        // แปลงค่ากลับเป็นตัวเลขก่อน
        let count1 = parseInt(this.onlineCount1.replace(/,/g, '')) || 0;
        let count2 = parseInt(this.onlineCount2.replace(/,/g, '')) || 0;
        let count3 = parseInt(this.onlineCount3.replace(/,/g, '')) || 0;
        let count4 = parseInt(this.onlineCount4.replace(/,/g, '')) || 0;
        let count5 = parseInt(this.onlineCount5.replace(/,/g, '')) || 0;
        let count6 = parseInt(this.onlineCount6.replace(/,/g, '')) || 0;
        let countAll = parseInt(this.onlineCountAll.replace(/,/g, '')) || 0;

        // สุ่มตัวเลขเพิ่มหรือลบ
        const randomChange = Math.random() > 0.5 ? 1 : -1;
        count1 += randomChange * Math.floor(Math.random() * 10);
        count2 += randomChange * Math.floor(Math.random() * 10);
        count3 += randomChange * Math.floor(Math.random() * 10);
        count4 += randomChange * Math.floor(Math.random() * 10);
        count5 += randomChange * Math.floor(Math.random() * 10);
        count6 += randomChange * Math.floor(Math.random() * 10);
        countAll += randomChange * Math.floor(Math.random() * 10);

        
        // ใช้ animateNumber เพื่ออัปเดตค่าตัวเลข
        this.onlineCount1 = count1.toLocaleString();
        this.onlineCount2 = count2.toLocaleString();
        this.onlineCount3 = count3.toLocaleString();
        this.onlineCount4 = count4.toLocaleString();
        this.onlineCount5 = count5.toLocaleString();
        this.onlineCount6 = count6.toLocaleString();

        this.animateNumber('onlineCountAll', parseInt(this.onlineCountAll.replace(/,/g, '')) || 0, countAll, () => {
          this.onlineCountAll = countAll.toLocaleString();
        });


    }, 3000); // อัปเดตทุกๆ 3 วินาที
  },
    nextSlide() {
    if (this.slides && this.slides.length > 0) {  // ตรวจสอบว่า slides ไม่เป็น undefined และมีค่า
      this.currentIndex = (this.currentIndex + 1) % this.slides.length;
    }
  },
  prevSlide() {
    if (this.slides && this.slides.length > 0) {  // ตรวจสอบว่า slides ไม่เป็น undefined และมีค่า
      this.currentIndex = (this.currentIndex - 1 + this.slides.length) % this.slides.length;
    }
  },
  goToSlide(index) {
    if (this.slides && this.slides.length > 0) {  // ตรวจสอบว่า slides ไม่เป็น undefined และมีค่า
      this.currentIndex = index;
    }
  },
  showCards() {
      const rwcontainer = document.getElementById("rw-container");
      rwcontainer.innerHTML = "";
      for (let i = 0; i < 4; i++) {
        const review = this.reviews[(this.rwindex + i) % this.reviews.length];
        const card = document.createElement("div");
        card.classList.add("rw-card");

      card.innerHTML = `
      <div class="rw-profile">
        <img src="${require(`@/assets/${review.img}`)}" alt="${review.user}"/>
        <b style="color:#FFD700">${review.user}</b>
      </div>
      <div class="rw-review-text">${review.text}</div>
      <div class="rw-stars">★★★★★</div>
    `;

        rwcontainer.appendChild(card);
      }
      this.rwindex = (this.rwindex + 4) % this.reviews.length;
    }
  },
  mounted() {
    this.updateOnlineCount();
  }
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
  background-color: #111;
}

.rw-container {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      grid-gap: 20px;
      background-color: rgba(18,34,41,0.3);
      width: 100%;
      max-width: 800px;
      overflow: hidden;
      text-align: left;
    }

    .rw-card {
      display: flex;
      flex-direction: column;
      background-color: rgba(18,34,41,1);
      border-radius: 8px;
      border: 0.5px solid #FFD700;
      padding: 10px;
      position: relative;
      overflow: hidden;
      opacity: 0;
      animation: rw-slideUp 0.5s ease-out forwards;
      box-shadow: 0 0 9px rgba(255, 215, 0, 0.6);
    }

    .rw-profile {
      display: flex;
      align-items: center;
      margin-bottom: 8px;
    }

    .rw-profile img {
      width: 50px;
      height: 50px;
      border-radius: 50%;
      margin-right: 10px;
      border: 2px solid #FFD700;
    }

    .rw-review-text {
      font-size: 14px;
      color: #fff;
      margin-bottom: 8px;
    }

    .rw-stars {
      color: #FFD700;
      font-size: 16px;
    }

    @keyframes rw-slideUp {
      0% { transform: translateY(-50%); opacity: 0; }
      100% { transform: translateY(0); opacity: 1; }
    }

.online-all {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 10px 20px;
  margin: 20px auto;
}

/* สไตล์ของ Online Status */
.user-online-status {
  display: flex;
  align-items: center;
  background-color: #fff;
  border: 1px solid gold; /* ขอบสีเขียว */
  border-radius: 30px; /* ให้มุมโค้ง */
  padding: 10px 30px;
  font-size: 16px;
  color: #ffffff; /* สีเขียว */
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1); /* เงาเบา */
  background-color: rgba(18, 34, 41, 0.3);
}

/* ไอคอนจุดสีเขียว */
.online-icon {
  font-size: 15px;
  color: #28a745; /* สีเขียว */
  margin-right: 10px;
  animation: pulse 1.5s infinite;
}

@keyframes pulse {
  0% {
    transform: scale(1); /* ขนาดเริ่มต้น */
    opacity: 1; /* ปกติ */
  }
  50% {
    transform: scale(0.5); /* ขยายขนาด */
    opacity: 0.7; /* ลดความทึบ */
  }
  100% {
    transform: scale(1); /* กลับสู่ขนาดเดิม */
    opacity: 1; /* กลับความทึบ */
  }
}

.online-num{
  color: gold;
  font-weight: bold;
}

/* คอนเทนเนอร์ของปุ่มทั้งสอง */
.button-container {
  display: flex;
  justify-content: center; /* จัดปุ่มให้อยู่กลาง */
  gap: 15px; /* ระยะห่างระหว่างปุ่ม */
  margin-top: 20px; /* เพิ่มระยะห่างจากข้อความ */
  flex-wrap: wrap; /* ให้ปุ่มเปลี่ยนบรรทัดเมื่อจอเล็ก */
  margin-bottom: 3.25rem;
}

.button-container a {
    text-decoration: none; /* เอาเส้นใต้ */
  }

/* ปุ่มสมัครสมาชิก */
.custom-button1 {
  background-color: gold; /* สีทอง */
  color: black; /* ตัวหนังสือสีดำ */
  padding: 20px 40px; /* ขยายขนาดปุ่ม */
  font-size: 18px; /* ขยายขนาดตัวหนังสือ */
  font-weight: bold;
  border: none;
  border-radius: 30px; /* ทำมุมมน */
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease, box-shadow 0.2s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px; /* ระยะห่างระหว่างไอคอนและข้อความ */
  box-shadow: 0px 4px 15px rgba(255, 215, 0, 0.6); /* เงาสีทอง */
  animation: bounce 2s infinite alternate; /* ทำให้ปุ่มกระเด้งๆ*/
}

/* สไตล์เมื่อ hover */
.custom-button1:hover {
  background-color: #ffcc00; /* เปลี่ยนสีเมื่อ hover */
  transform: scale(1.1); /* ขยายขนาดเล็กน้อยเมื่อ hover */
  box-shadow: 0px 8px 25px rgba(255, 215, 0, 0.8); /* เงาที่ใหญ่ขึ้นเมื่อ hover */
}

/* สไตล์เมื่อคลิก */
.custom-button1:active {
  transform: translateY(3px); /* ลดขนาดลงเล็กน้อยเมื่อคลิก */
  box-shadow: 0px 2px 10px rgba(255, 215, 0, 0.4); /* ลดเงาลงเมื่อคลิก */
}

/* การแอนิเมชันกระเด้ง */
@keyframes bounce {
  0% {
    transform: scale(1); /* ขนาดเริ่มต้น */
  }
  50% {
    transform: scale(1.05); /* ขยายขนาดเล็กน้อย */
  }
  100% {
    transform: scale(1); /* กลับสู่ขนาดเดิม */
  }
}

.custom-button1 i {
  font-size: 24px; /* ขนาดไอคอน */
}

/* ปุ่มติดต่อแอดมิน */
.custom-button2 {
  background-color: #00C300; /* สีเขียวแบบไลน์ */
  color: white;
  padding: 20px 40px; /* ขยายขนาดปุ่ม */
  font-size: 18px;
  font-weight: bold;
  border: none;
  border-radius: 30px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease; /* เอฟเฟกต์การเปลี่ยนสี */
  box-shadow: 0px 4px 15px rgba(0, 200, 0, 0.6); /* เงาสีเขียว */
}

.custom-button2:hover {
  background-color: #33CC33; /* เปลี่ยนเป็นเขียวอ่อนเมื่อ hover */
  transform: translateY(-3px); /* เพิ่มการเคลื่อนไหวเล็กน้อย */
  box-shadow: 0px 6px 20px rgba(0, 200, 0, 0.8); /* เพิ่มขนาดเงาเมื่อ hover */
}

.custom-button2:active {
  transform: translateY(1px); /* ลดการเคลื่อนไหวเล็กน้อยเมื่อคลิก */
  box-shadow: 0px 2px 10px rgba(0, 200, 0, 0.4); /* ลดขนาดเงาเมื่อ active */
}

/* ปรับขนาดและจัดตำแหน่งปุ่มเมื่อหน้าจอเล็ก */


/* สไตล์สำหรับรูป */
.img-logo {
  max-width: 70%;
  filter: drop-shadow(0 0 10px rgba(255, 215, 0, 1));
}

/* ข้อความที่กระพริบ */
.text1 {
  font-size: 2.2rem;
  font-weight: bold;
  color: white;
  text-align: center;
  display: inline-block;
  padding: 10px;
  border-radius: 5px;
  margin-bottom: 1.5rem;
  animation: blink 1s infinite alternate; /* ทำให้กระพริบ */
  animation-delay: 2s;
  text-shadow: 2px 2px 5px rgba(255, 215, 0, 0.8), 0 0 25px gold, 0 0 5px darkgoldenrod;
}

.text2{
  color: white;
}

.text3 {
  font-size: 2.2rem;
  font-weight: bold;
  color: gold;
  text-align: center;
  display: inline-block;
  padding: 10px;
  border-radius: 5px;
  margin-top: 2.25rem;
  margin-bottom: 1.5rem;
  animation: blink 1s infinite alternate; /* ทำให้กระพริบ */
  animation-delay: 2s;
  text-shadow: 2px 2px 5px rgba(255, 215, 0, 0.8), 0 0 25px gold, 0 0 5px darkgoldenrod;
}

.text4 {
  font-size: 2.2rem;
  font-weight: bold;
  color: gold;
  text-align: center;
  display: inline-block;
  padding: 10px;
  border-radius: 5px;
  margin-top: 2.25rem;
  animation: blink 1s infinite alternate; /* ทำให้กระพริบ */
  animation-delay: 2s;
  text-shadow: 2px 2px 5px rgba(255, 215, 0, 0.8), 0 0 25px gold, 0 0 5px darkgoldenrod;
}


/* Animation สำหรับการกระพริบ */
@keyframes blink {
  0% {
    opacity: 1; /* ปกติ */
  }
  50% {
    opacity: 0.7; /* กระพริบลดความทึบ */
  }
  100% {
    opacity: 1; /* ปกติ */
  }
}

     .container2 {
  width: 40%; /* กำหนดความกว้างเป็น 50% */
  margin: 0 auto; /* จัดตำแหน่งให้อยู่ตรงกลาง */
  padding: 10px 30px; 
  background-color: rgba(18, 34, 41, 0.3);
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(255, 215, 0, 0.7); /* เงาสีทอง */
  display: flex;
  flex-direction: column-reverse;
  align-items: center; /* จัดแนวกลางแนวตั้ง */
  justify-content: center; /* จัดแนวกลางแนวนอน */
  position: relative; /* เพิ่มตำแหน่งที่สัมพันธ์กับการจัด layout */
  height: auto; /* สูงของคอนเทนเนอร์จะยืดตามเนื้อหา */
}

  @media (max-width: 978px) {
  .container2 {
    width: 95%; /* เปลี่ยนความกว้างเป็น 95% เมื่อความกว้างของหน้าจอน้อยกว่า 978px */
    box-sizing: border-box;
  }
}

    .amount {
  color: gold; /* สีทอง */
  font-weight: bold; /* ตัวหนา */
}

    .card-two {
      width: 100%;
      position: relative;
      flex: 1 0 20%;
      padding: 10px 15px;
      margin: 5px 0;
      background-color: rgba(18, 34, 41, 1);
      border-radius: 8px;
      border: 0.5px solid gold; /* เส้นขอบสีทอง */
      display: flex;
      justify-content: space-between;
      overflow: hidden;
      opacity: 0;
      animation: slideUp 0.5s ease-out forwards;
    }

    /* เอฟเฟกต์คลื่นแสงสีทอง */
    .card-two::before {
      content: "";
      position: absolute;
      top: 0;
      left: -150%;
      width: 150%;
      height: 100%;
      background: linear-gradient(
        120deg,
        transparent 0%,
        rgba(255, 215, 0, 0.2) 50%,
        transparent 100%
      );
      transform: skewX(-20deg);
      animation: shimmer 3s linear infinite;
      pointer-events: none;
      z-index: 1;
    }

    .card-two.speed1::before { animation-duration: 2s; }
    .card-two.speed2::before { animation-duration: 3s; }
    .card-two.speed3::before { animation-duration: 4s; }

    @keyframes shimmer {
      0% { left: -150%; }
      100% { left: 150%; }
    }

    .card-left {
      flex: 0 0 60%;
      display: flex;
      align-items: center;
      justify-content: flex-start;
      z-index: 2;
    }

    .card-right {
      font-size: 15px;
      color: #FFFFFF;
      flex: 0 0 40%;
      display: flex;
      justify-content: flex-end;
      align-items: center;
      gap: 5px;
      z-index: 2;
    }

    .logo-section {
      margin-right: 10px;
    }

    .user-info, .transaction-info {
      font-size: 15px;
      color: white;
      text-align: left;
    }

    .loading-icon {
      width: 20px;
      height: 20px;
      border: 3px solid transparent;
      border-top: 3px solid gold; /* ขอบบนหมุนสีทอง */
      border-radius: 50%;
      animation: spin 1s linear infinite;
    }

    .check-icon {
      font-size: 20px;
      color: gold;
      display: none;
    }

    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    @keyframes slideUp {
      0% {
        transform: translateY(-100%);
        opacity: 0;
      }
      100% {
        transform: translateY(0);
        opacity: 1;
      }
    }

      /* Container for Cards */
    .card-container {
      display: grid;
      grid-template-columns: repeat(3, 1fr); /* 3 cards in one row */
      gap: 20px;
      padding: 20px;
      width: 90%;
      max-width: 1200px;
      margin: 0 auto; /* Align the container to the center */
    }

    .card {
        position: relative; /* For better control of positioning */
        width: 100%; /* Make the card full-width */
        min-height: 300px;
        overflow: hidden; /* Hide any overflow content */
        border-radius: 15px; /* Optional: rounded corners */
        border: 1px solid gold; /* เส้นขอบสีทอง */
        cursor: pointer;
        opacity: 0.9;
        transition: transform 0.3s ease, box-shadow 0.3s ease;
    }

    /* Card Hover Effect */
    .card:hover {
      transform: translateY(-10px);
      box-shadow: 0 6px 20px rgba(0, 0, 0, 0.2);
    }

    .badge {
  position: absolute;
  top: 10px;
  right: 10px;
  padding: 10px 15px;
  background-color: red; /* พื้นหลังสีแดง */
  color: white;
  font-weight: bold;
  border-radius: 5px;
  font-size: 14px; /* ขนาดฟอนต์ */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2); /* เงาเบา ๆ เพื่อให้ข้อความดูเด่น */
  transition: background-color 0.3s ease; /* เพิ่มการเปลี่ยนสีเมื่อ hover */
  
  /* การกระพริบ */
  animation: blink 1.5s infinite alternate;
}

  .badge:hover {
    background-color: #d9534f; /* สีแดงเข้มเมื่อ hover */
  }

    .online-status {
      width: 100%;
      position: absolute;
      bottom: 0; /* อยู่ที่ด้านล่างสุด */
      left: 50%; /* จัดตำแหน่งแนวนอนให้ตรงกลาง */
      transform: translateX(-50%); /* ปรับตำแหน่งให้ข้อความอยู่ตรงกลาง */
      color: #ffffff; /* เปลี่ยนเป็นสีเขียว */
      font-weight: bold;
      font-size: 1.25rem;
      padding: 10px 0;
      text-shadow: 2px 2px 4px rgba(255, 252, 49, 0.5);
      background-color: transparent; /* ไม่ให้มีพื้นหลัง */
      transition: color 0.3s ease; /* เพิ่มการเปลี่ยนสีเมื่อ hover */
    }

    
.chance-status {
   width: 100%;
  position: absolute;
  bottom: 15%; /* อยู่ที่ด้านล่างสุด */
  left: 50%;
  transform: translateX(-50%); /* จัดให้ตรงกลาง */
  color: rgb(255, 227, 67); /* สีแดง */
  font-weight: bold;
  font-size: 1.35rem;
  text-shadow: 2px 2px 4px rgba(255, 252, 49, 0.5);
  animation: blink 0.7s infinite; /* เรียกใช้งาน animation */
}

    .img-game1 {
      width: 100%; /* ให้ภาพเต็มความกว้าง */
      height: 100%; /* ให้ภาพเต็มความสูง */
      object-fit: cover; /* รักษาสัดส่วนและครอบพื้นที่ */
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 0.6) 100%), url('@/assets/photo_6165509241302009692_y.jpg'); /* เพิ่มกราเดียนต์ที่มีความทึบที่ด้านล่าง */
      background-size: cover; /* ครอบภาพเต็มพื้นที่ */
      background-position: center center; /* จัดตำแหน่งภาพให้อยู่กลาง */
    }

    .img-game2 {
      width: 100%; /* ให้ภาพเต็มความกว้าง */
      height: 100%; /* ให้ภาพเต็มความสูง */
      object-fit: cover; /* รักษาสัดส่วนและครอบพื้นที่ */
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 0.6) 100%), url('@/assets/photo_6165509241302009702_y.jpg'); /* เพิ่มกราเดียนต์ที่มีความทึบที่ด้านล่าง */
      background-size: cover; /* ครอบภาพเต็มพื้นที่ */
      background-position: center center; /* จัดตำแหน่งภาพให้อยู่กลาง */
    }

    .img-game3 {
      width: 100%; /* ให้ภาพเต็มความกว้าง */
      height: 100%; /* ให้ภาพเต็มความสูง */
      object-fit: cover; /* รักษาสัดส่วนและครอบพื้นที่ */
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 0.6) 100%), url('@/assets/photo_6165509241302009694_y.jpg'); /* เพิ่มกราเดียนต์ที่มีความทึบที่ด้านล่าง */
      background-size: cover; /* ครอบภาพเต็มพื้นที่ */
      background-position: center center; /* จัดตำแหน่งภาพให้อยู่กลาง */
    }

    .img-game4 {
      width: 100%; /* ให้ภาพเต็มความกว้าง */
      height: 100%; /* ให้ภาพเต็มความสูง */
      object-fit: cover; /* รักษาสัดส่วนและครอบพื้นที่ */
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 0.6) 100%), url('@/assets/photo_6165509241302009695_y.jpg'); /* เพิ่มกราเดียนต์ที่มีความทึบที่ด้านล่าง */
      background-size: cover; /* ครอบภาพเต็มพื้นที่ */
      background-position: center center; /* จัดตำแหน่งภาพให้อยู่กลาง */
    }

    .img-game5 {
      width: 100%; /* ให้ภาพเต็มความกว้าง */
      height: 100%; /* ให้ภาพเต็มความสูง */
      object-fit: cover; /* รักษาสัดส่วนและครอบพื้นที่ */
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 0.6) 100%), url('@/assets/photo_6165509241302009696_y.jpg'); /* เพิ่มกราเดียนต์ที่มีความทึบที่ด้านล่าง */
      background-size: cover; /* ครอบภาพเต็มพื้นที่ */
      background-position: center center; /* จัดตำแหน่งภาพให้อยู่กลาง */
    }

    .img-game6 {
      width: 100%; /* ให้ภาพเต็มความกว้าง */
      height: 100%; /* ให้ภาพเต็มความสูง */
      object-fit: cover; /* รักษาสัดส่วนและครอบพื้นที่ */
      background: linear-gradient(to bottom, rgba(0, 0, 0, 0) 0%, rgba(0, 0, 0, 0.6) 100%), url('@/assets/photo_6165509241302009697_y.jpg'); /* เพิ่มกราเดียนต์ที่มีความทึบที่ด้านล่าง */
      background-size: cover; /* ครอบภาพเต็มพื้นที่ */
      background-position: center center; /* จัดตำแหน่งภาพให้อยู่กลาง */
    }

    /* Card Title */
    .card-title {
      font-size: 1.5rem;
      font-weight: bold;
      margin-bottom: 10px;
      color: #333;
    }

    .card-description {
      position: absolute; /* Absolute positioning inside card */
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      overflow: hidden;
    }
    /* Responsive Design for smaller screens */
    @media (max-width: 768px) {
      .card-container {
        grid-template-columns: repeat(2, 1fr); /* 2 cards in one row */
      }
      .card {
        min-height: 220px;
    }
     .card-container {
      gap: 15px;
      padding: 1px;
      width: 100%;
    }
    }

    @media (max-width: 480px) {
      .online-status {
      font-size: 1.1rem;
    }
    
      .chance-status {
        font-size: 1.1rem;
      }
    }

    .slider-container {
      position: relative;
      width: 100%;
      max-width: 600px; /* ปรับตามความต้องการ */
      height: 60%;
      margin: auto;
      margin-top: 2.25rem;
      margin-bottom: 2.25rem;
      overflow: hidden;
      border-radius: 15px;
      border: 2px solid #FFD700;
      box-shadow: 0 0 20px rgba(255, 215, 0, 0.6);
    }

    .slider {
      display: flex;
      transition: transform 1s ease;
    }

    .slide {
      min-width: 100%;
      height: 60%;
      position: relative;
    }

    .slide img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      border-radius: 15px;
    }

    .dots-container {
      position: absolute;
      bottom: 10px;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      gap: 10px;
    }

    .dot {
      width: 12px;
      height: 12px;
      border-radius: 50%;
      background-color: #FFD700;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }

    .dot.active {
      background-color: #FFCC00;
    }
    
    .ranking-container {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      grid-gap: 10px;
      padding: 10px;
      background-color: rgba(18, 34, 41, 0.3);
      border-radius: 12px;
      width: 100%;
      max-width: 800px; /* ความกว้างสูงสุด */
      overflow: hidden;
      box-shadow: 0 4px 10px rgba(255, 215, 0, 0.7);
      box-sizing: border-box;
      text-align: left;
    }

    .ranking-card {
      padding: 10px 15px;
      background-color: rgba(18, 34, 41, 1);
      border-radius: 8px;
      border: 0.5px solid #FFD700;
      display: flex;
      justify-content: space-between;
      overflow: hidden;
      opacity: 0;
      animation: slideInCard 0.5s ease-out forwards;
      position: relative;
    }

    .ranking-card::before {
      content: "";
      position: absolute;
      top: 0;
      left: -150%;
      width: 150%;
      height: 100%;
      background: linear-gradient(
        120deg,
        transparent 0%,
        rgba(255, 215, 0, 0.2) 50%,
        transparent 100%
      );
      transform: skewX(-20deg);
      animation: shimmerWave 3s linear infinite;
      pointer-events: none;
      z-index: 1;
    }

    .ranking-card.fast-wave::before { animation-duration: 2s; }
    .ranking-card.medium-wave::before { animation-duration: 3s; }
    .ranking-card.slow-wave::before { animation-duration: 4s; }

    @keyframes shimmerWave {
      0% { left: -150%; }
      100% { left: 150%; }
    }

    .card-details {
      flex: 0 0 100%;
      display: flex;
      align-items: center;
      justify-content: flex-start;
      z-index: 2;
    }

    /* .rank-info {
      font-size: 12px;
      color: #FFFFFF;
      flex: 0 0 40%;
      display: flex;
      justify-content: flex-end;
      align-items: center;
      gap: 5px;
      z-index: 2;
    } */

    .user-name, .user-transaction {
      font-size: 15px;
      color: white;
    }

    @keyframes slideInCard {
      0% {
        transform: translateY(-100%);
        opacity: 0;
      }
      100% {
        transform: translateY(0);
        opacity: 1;
      }
    }
</style>
