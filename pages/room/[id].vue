<script setup>
const router = useRouter();
const route = useRoute();
const room = ref({});


const id = route.params.id;
const api = `https://nuxr3.zeabur.app/api/v1/rooms/${id}`;

const getRoom = async () => {
  try {
    const getData = await fetch(api);
    const { result } = await getData.json();
    room.value = result;
  } catch(error) {
    alert(error);
  }
};

getRoom();
</script>

<template>
  <h2>房型詳細頁面</h2>

  <div class="container">
    <button @click="router.go(-1)">回上一頁</button>
    <div class="row justify-content-center">
      <div class="col-md-6">
        <div class="room-page">
          <div class="room-header">
            <h1 class="room-name">{{room.name}}</h1>
            <p class="room-description">
              {{room.description}}
            </p>
          </div>

          <div class="room-gallery">
            <img
              :src="room.imageUrl"
              alt="尊爵雙人房主圖"
              class="room-main-image"
            />
            <div class="room-image-list">
              <img
                v-for="item in room.imageUrlList"
                :key="item"
                :src="item"
                alt="圖片2"
              />
            </div>
          </div>

          <div class="room-info">
            <div class="info-block">
              <h2>房間資訊</h2>
              <p>面積: 24坪</p>
              <p>床型: 一張大床</p>
              <p>最多容納人數: 4</p>
              <p>價格: NT$10,000</p>
            </div>

            <div class="info-block">
              <h2>房間配置</h2>
              <ul>
                <li>市景: 提供</li>
                <li>獨立衛浴: 提供</li>
                <li>樓層電梯: 提供</li>
              </ul>
            </div>

            <div class="info-block">
              <h2>房內設施</h2>
              <ul>
                <li>平面電視: 提供</li>
                <li>吹風機: 提供</li>
                <li>冰箱: 提供</li>
                <li>熱水壺: 提供</li>
                <li>檯燈: 提供</li>
                <li>衣櫥: 提供</li>
                <li>書桌: 提供</li>
              </ul>
            </div>

            <div class="info-block">
              <h2>客房備品</h2>
              <ul>
                <li>衛生紙: 提供</li>
                <li>拖鞋: 提供</li>
                <li>沐浴用品: 提供</li>
                <li>刮鬍刀: 提供</li>
                <li>刷牙用品: 提供</li>
                <li>罐裝水: 提供</li>
                <li>梳子: 提供</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.room-page {
  max-width: 1200px;
  margin: 0 auto;
  background-color: #fff;
  padding: 20px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
}

.room-header {
  text-align: center;
  margin-bottom: 30px;
}

.room-name {
  font-size: 2rem;
  color: #333;
}

.room-description {
  font-size: 1rem;
  color: #666;
}

.room-gallery {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 30px;
}

.room-main-image {
  width: 100%;
  max-width: 600px;
  height: auto;
  border-radius: 10px;
  margin-bottom: 20px;
}

.room-image-list {
  display: flex;
  justify-content: center;
  gap: 10px;
}

.room-image-list img {
  width: 100px;
  height: auto;
  border-radius: 5px;
  cursor: pointer;
  transition: transform 0.3s;
}

.room-image-list img:hover {
  transform: scale(1.1);
}

.room-info {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.info-block {
  background-color: #f0f0f0;
  padding: 15px;
  border-radius: 10px;
}

.info-block h2 {
  font-size: 1.5rem;
  margin-bottom: 10px;
  color: #444;
}

.info-block p,
.info-block ul {
  font-size: 1rem;
  color: #555;
}

.info-block ul {
  list-style: none;
  padding-left: 0;
}

.info-block ul li {
  margin-bottom: 5px;
}
</style>
