
<template>
  <q-page padding>
    <div class="text-h4 q-mb-md">
      Version Control + Docker Demo (Quasar)
    </div>

    <!-- Git Workflow -->
    <q-card class="q-mb-md">
      <q-card-section>
        <div class="text-h6">
          Git Workflow (ตัวอย่างขั้นตอนทำงาน)
        </div>

        <q-list bordered separator class="q-mt-sm">
          <q-item
            v-for="(step, index) in gitSteps"
            :key="index"
          >
            <q-item-section avatar>
              <q-badge>{{ index + 1 }}</q-badge>
            </q-item-section>

            <q-item-section>
              <q-item-label>{{ step.title }}</q-item-label>
              <q-item-label caption>
                {{ step.detail }}
              </q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-card-section>
    </q-card>

    <!-- Docker Concepts -->
    <q-card class="q-mb-md">
      <q-card-section>
        <div class="text-h6">
          Docker Concepts (สรุปสั้น ๆ)
        </div>

        <q-list bordered separator class="q-mt-sm">
          <q-item
            v-for="(item, index) in dockerItems"
            :key="index"
          >
            <q-item-section>
              <q-item-label>{{ item.title }}</q-item-label>
              <q-item-label caption>
                {{ item.detail }}
              </q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-card-section>
    </q-card>

    <!-- Docker Quick Reference -->
    <q-card class="q-mb-md">
      <q-card-section>
        <div class="text-h6">
          Docker Quick Reference
        </div>

        <div class="text-caption text-grey q-mb-sm">
          รวมคำสั่ง Docker ที่ใช้บ่อย พร้อมคำอธิบายภาษาไทย
        </div>

        <q-list bordered separator>
          <q-item
            v-for="(item, index) in dockerCommands"
            :key="index"
          >
            <q-item-section>
              <q-item-label class="text-weight-bold">
                {{ item.title }}
              </q-item-label>

              <q-item-label class="text-primary q-my-xs">
                {{ item.command }}
              </q-item-label>

              <q-item-label caption>
                {{ item.detail }}
              </q-item-label>
            </q-item-section>
          </q-item>
        </q-list>
      </q-card-section>
    </q-card>

  </q-page>
</template>

<script setup>
const gitSteps = [
  {
    title: 'แก้โค้ด Quasar ใน src/',
    detail: 'เพิ่มหน้า / component ใหม่ เช่น IndexPage.vue, Layout ต่าง ๆ',
  },
  {
    title: 'ตรวจสอบสถานะไฟล์',
    detail: 'ใช้คำสั่ง git status ดูว่าไฟล์ไหนเปลี่ยนแปลงบ้าง',
  },
  {
    title: 'เพิ่มไฟล์เข้า staging',
    detail: 'จากรากโปรเจกต์ ใช้ git add frontend/src/pages/IndexPage.vue',
  },
  {
    title: 'สร้าง commit พร้อมข้อความแบบ Conventional Commits',
    detail: 'เช่น feat: add Git workflow demo page',
  },
  {
    title: 'push ขึ้น GitHub',
    detail: 'ใช้ git push -u origin feature/quasar-demo แล้วเปิด Pull Request',
  },
]

const dockerItems = [
  {
    title: 'Image',
    detail: 'แพ็กเกจที่มีไฟล์และการตั้งค่าที่ใช้สร้าง container เช่น image ที่รวม Quasar SPA กับ Nginx',
  },
  {
    title: 'Container',
    detail: 'อินสแตนซ์ที่สร้างจาก image เช่น container ที่รัน Nginx เพื่อเสิร์ฟไฟล์ Quasar',
  },
  {
    title: 'Volume',
    detail: 'เก็บข้อมูลให้คงอยู่แยกจากวงจรชีวิตของ container เช่น ไฟล์อัปโหลดของ backend',
  },
  {
    title: 'Network',
    detail: 'ให้บริการใน Docker ติดต่อกันได้ เช่น Nginx ส่งต่อคำขอไปยัง Express',
  },
]

const dockerCommands = [
  {
    title: '1. Build Docker Image',
    command: 'docker build -t quasar-demo ./frontend',
    detail: 'ใช้สร้าง Docker Image จาก Dockerfile ภายในโฟลเดอร์ frontend เมื่อต้องการสร้าง Image ใหม่',
  },
  {
    title: '2. Run Container',
    command: 'docker run -d -p 8080:80 quasar-demo',
    detail: 'ใช้สร้างและเปิด Container จาก Image โดยให้เข้าถึงเว็บไซต์ผ่านพอร์ต 8080',
  },
  {
    title: '3. Check Running Containers',
    command: 'docker ps',
    detail: 'ใช้ตรวจสอบว่า Container ตัวไหนกำลังทำงานอยู่ พร้อมดูพอร์ตที่เปิดใช้งาน',
  },
  {
    title: '4. Start Docker Compose',
    command: 'docker compose up -d --build',
    detail: 'ใช้สร้าง Image และเริ่มทำงานทุก Service ตามไฟล์ docker-compose.yml ในโหมดเบื้องหลัง',
  },
  {
    title: '5. Stop Docker Compose',
    command: 'docker compose down',
    detail: 'ใช้หยุดและลบ Container รวมถึง Network ที่สร้างโดย Docker Compose',
  },
  {
    title: '6. View Container Logs',
    command: 'docker compose logs -f frontend',
    detail: 'ใช้ดู Log ของ Service frontend แบบต่อเนื่อง เพื่อตรวจสอบข้อผิดพลาดระหว่างทำงาน',
  },
]
</script>
