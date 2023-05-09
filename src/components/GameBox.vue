<script>
import { Box, Camera, LambertMaterial, PointLight, Renderer, Scene } from 'troisjs';
import { onKeyStroke } from '@vueuse/core'


export default {
  components: { Box, Camera, LambertMaterial, PointLight, Renderer, Scene }, 
  methods: {
    onPointerEvent(event) {
      console.log(event);
    },
    onPointerOver(event) {
      event.component.mesh.material.color.set(event.over ? 0xff0000 : 0xffffff);
    },
  },
  mounted() {
    const renderer = this.$refs.renderer;
    const box = this.$refs.box.mesh;
    const box2 = this.$refs.box2.mesh;
    const box3 = this.$refs.box3.mesh;

    renderer.onBeforeRender(() => {
      box.rotation.x += 0.01;
      box2.rotation.y += 0.01;
      box3.rotation.z += 0.01;
    });

    onKeyStroke('ArrowDown', (e) => {
        e.preventDefault();
        console.log("Key pressed");
        box.position.y -= 0.1;
    });
    onKeyStroke('ArrowUp', (e) => {
        e.preventDefault();
        console.log("Key pressed");
        box.position.y += 0.1;
    });
    onKeyStroke('ArrowLeft', (e) => {
        e.preventDefault();
        console.log("Key pressed");
        box.position.x -= 0.1;
    });
    onKeyStroke('ArrowRight', (e) => {
        e.preventDefault();
        console.log("Key pressed");
        box.position.x += 0.1;
    });
  }, 
}
</script>

<template>
    <div class="render">
        <Renderer ref="renderer" resize="true">
            <Camera :position="{ z: 10 }" />
            <Scene>
                <PointLight :position="{ y: 50, z: 50 }" />
                <Group>
                    <Box ref="box"  :position="{x: -5}" :rotation="{ y: Math.PI / 4, z: Math.PI / 4 }"   @pointerEnter="onPointerEvent" @pointerOver="onPointerOver">
                        <LambertMaterial />
                    </Box>
                    <Box ref="box2" :position="{x:0}" :rotation="{ y: Math.PI / 4, z: Math.PI / 4 }">
                        <LambertMaterial />
                    </Box>
                    <Box ref="box3" :position="{x:5}" :rotation="{ y: Math.PI / 4, z: Math.PI / 4 }">
                        <LambertMaterial />
                    </Box>
                </Group>
               
            </Scene>
        </Renderer>
    </div>
</template>

<style scoped>

.render{
    height: 100vh;
    width: 100vw;
}
</style>