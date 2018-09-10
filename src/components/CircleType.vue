<template>
  <svg width="800" height="400"></svg>
</template>

<script>
  import * as d3 from 'd3'

  export default {
    name: 'CircleType',
    props: ['shape', 'text'],
    data () {
      return {
        mainShape: {
          x: 600,         // X value
          y: 200,         // Y value
          r: 150,         // radius of circle
          bg: '#00FF00'   // background color
        }
      }
    },
    watch: {
      text () {
        this.clear()
        this.draw()
      }
    },
    mounted () {
      this.calculateShapes(this.shape)
      this.draw()
    },
    methods: {
      calculateShapes (shapeArr) {
        const that = this
        this.mainShapeArr = shapeArr.map(shape => Object.assign({}, that.mainShape, shape))
      },
      draw () {
        const svg = d3.select(this.$el)
        const g = svg.selectAll('g')
          .data(this.mainShapeArr)
          .enter()
          .append('g')
          .attr('transform', d => `translate(${d.x},${d.y})`)

        g.append('circle')
          .attr('r', d => d.r)
          .attr('stroke', 'black')
          .attr('fill', d => d.bg)

        g.append('text')
          .attr('style', 'text-anchor: middle')
          .text(this.text)
      },
      clear () {
        d3.select(this.$el).selectAll('g').remove()
      }
    }
  }
</script>

<style scoped>
  svg {
    -webkit-box-shadow: 0px 1px 12px 1px rgba(0,0,0,0.75);
    -moz-box-shadow: 0px 1px 12px 1px rgba(0,0,0,0.75);
    box-shadow: 0px 1px 12px 1px rgba(0,0,0,0.75);
  }
</style>