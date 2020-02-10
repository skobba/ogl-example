        // Load a glTF resource
        loader.load(
            // resource URL
            'Avocado.glb',
            // called when the resource is loaded
            function ( gltf ) {

                scene.add( gltf.scene );

                gltf.animations; // Array<THREE.AnimationClip>
                gltf.scene; // THREE.Scene
                gltf.scenes; // Array<THREE.Scene>
                gltf.cameras; // Array<THREE.Camera>
                gltf.asset; // Object

            },
            // called while loading is progressing
            function ( xhr ) {

                console.log( ( xhr.loaded / xhr.total * 100 ) + '% loaded' );

            },
            // called when loading has errors
            function ( error ) {

                console.log( 'An error happened' );

            }
        );



        var loader = new THREE.GLTFLoader();
        loader.load("./law_model.glb",
        function ( gltf ) {
            var scale = 5.6;
            bus.body = gltf.scene.children[0];
            bus.body.name = "body";
            bus.body.rotation.set ( 0, -1.5708, 0 );
            bus.body.scale.set (scale,scale,scale);
            bus.body.position.set ( 0, 3.6, 0 );
            bus.body.castShadow = true;
            bus.frame.add(bus.body);
        },
        );
        scene.add( bus.frame )

        camera.position.z = 5;


        