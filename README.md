    // Light
    const light = new THREE.PointLight(0xffffff, 1);
    light.position.set(10, 10, 10);
    scene.add(light);

    const ambientLight = new THREE.AmbientLight(0x404040);
    scene.add(ambientLight);

    // Heart Geometry
    const heartShape = new THREE.Shape();
    heartShape.moveTo(0, 0);
    heartShape.bezierCurveTo(0, 0, -1, 1.5, 0, 3);
    heartShape.bezierCurveTo(1, 1.5, 0, 0, 0, 0);

    const geometry = new THREE.ExtrudeGeometry(heartShape, { depth: 1, bevelEnabled: true, bevelSegments: 2, steps: 2, bevelSize: 0.2, bevelThickness: 0.2 });
    const material = new THREE.MeshPhongMaterial({ color: 0xff0000, shininess: 100 });
    const heart = new THREE.Mesh(geometry, material);
    scene.add(heart);

    heart.rotation.x = Math.PI; // พลิกหัวใจให้ตรง

    camera.position.z = 5;

    // Animation
    function animate() {
    requestAnimationFrame(animate);
    heart.rotation.y += 0.01;
    renderer.render(scene, camera);
    }
    animate();

    // Resize
    window.addEventListener('resize', () => {
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
    renderer.setSize(window.innerWidth, window.innerHeight);
    });
</script>
