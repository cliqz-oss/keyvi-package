Step by step commands to build a new package for EMR

    sudo yum install git
    git clone https://github.com/cliqz-oss/keyvi.git
    cd keyvi/contrib
    sudo bash prepare_amazon_linux_buildenv.sh 
    sudo bash build_boost_static.sh
    sudo bash build_snappy_static.sh
    cd ../keyvi
    scons
    
