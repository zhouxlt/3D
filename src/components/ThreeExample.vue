<template>
  <div class="3d">
    <div class="container"></div>
  </div>
</template>

<script>
import * as Three from 'three'
export default {
  name: 'ThreeExample',
  components: {
  },
  data () {
    return {
      camera: null,
      scene: null,
      renderer: null,
      mesh: null
    }
  },
  methods: {
    init () {
      // let container = document.getElementById('container')

      // this.camera = new Three.PerspectiveCamera(70, container.clientWidth/container.clientHeight, 0.01, 10)
      this.camera = new Three.PerspectiveCamera(70, window.innerWidth/window.innerHeight, 0.01, 10)
      this.camera.position.z = 1

      this.scene = new Three.Scene()

      let geometry = new Three.BoxGeometry(0.2, 0.2, 0.2)
      let material = new Three.MeshNormalMaterial()

      this.mesh = new Three.Mesh(geometry, material)
      this.scene.add(this.mesh)

      this.renderer = new Three.WebGLRenderer({antialias: true})
      // this.renderer.setSize(container.clientWidth, container.clientHeight)
      this.renderer.setSize(window.innerWidth, window.innerHeight)
      // container.appendChild(this.renderer.domElement)
      document.body.appendChild(this.renderer.domElement)
    },
    animate () { 
      requestAnimationFrame(this.animate)
      this.mesh.rotation.x += 0.01
      this.mesh.rotation.y += 0.02
      this.renderer.render(this.scene, this.camera)
    }
  },
  mounted() {
    window.onresize = () => {
      this.renderer.setSize(window.innerWidth, window.innerHeight)
      this.camera.aspect=window.innerWidth/window.innerHeight
      this.camera.updateProjectionMatrix()
    }
    this.init()
    this.animate()
  }

}
</script>