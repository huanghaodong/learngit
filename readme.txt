import React,{Component} from 'react';
import {
  AppRegistry,
  AsyncStorage,
  Button,
  StyleSheet,
  Text,
  View,
  ListView,
  TouchableWithoutFeedback
} from 'react-native';
import Swipeout from 'react-native-swipeout';
const rows = [1,2,3,4,5,6,7,8,9];
class deleteMe extends Component {

  constructor() {
    super();

    var ds = new ListView.DataSource({rowHasChanged: (row1, row2) => row1!==row2});

    this.state = {
      dataSource: ds.cloneWithRows(rows),
      rowID: '',
      sectionID:''
    };
  }

  _renderRow(rowData, sectionID, rowID) {
    return (
      <Swipeout
        close={!(this.state.sectionID === sectionID && this.state.rowID === rowID)}//点其他行就关闭当前行的swipe
        right={[{text:'button'}]}
        rowID={rowID}
        sectionID={sectionID}
        autoClose={true}
        backgroundColor={'#fff'}
        onOpen={(sectionID,rowID) => {
          console.log(1)
          this.setState({
            sectionID,
            rowID,

          })
        }}

      >
        <TouchableWithoutFeedback onPress={() => console.log('press children')}>
          <View style={styles.li} >
            <Text>{rowData}</Text>
          </View>
        </TouchableWithoutFeedback>
      </Swipeout>
    );
  }

  render() {
    return (
      <View style={styles.container}>
        <ListView
          scrollEnabled
          dataSource={this.state.dataSource}
          renderRow={this._renderRow.bind(this)}
        />
      </View>
    );
  }

}

const styles = StyleSheet.create({
  container:{
    backgroundColor:'#fff',
    flex:1
  },
  li:{
    height:60,
    borderColor:'#000',
    borderBottomWidth:1
  }
})
AppRegistry.registerComponent('deleteMe', () => deleteMe);
ny地方5555555555aSasasasasfdsf sdf dsf sdf sd f如果奋斗过的 