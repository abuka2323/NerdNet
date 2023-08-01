# NerdNet
MERN FULLSTACK APP


This MERN Social Media App is a full-featured social media application that includes user authentication, profile management, post creation, likes, comments, and a real-time chat system. This project demonstrates the ability to create a complex, full-stack application using modern web development technologies.


Clone the repository: 
git clone https://github.com/abuka2323/mern-social-media.git 


 ---> cd server --> npm install
> cd client --> npm install

 to run locally --> npm start 
 
const DataFetcher = require('./dataFetcher'); // Import the DataFetcher class
const { jest } = require('@jest/globals'); // Import Jest's mocking capabilities

describe('DataFetcher', function() {
  const mockModel = {
    getValue: jest.fn(),
  };

  const dataFetcher = new DataFetcher(mockModel);

  it('should fetch page JSON from MCM API', async function() {
    const nodeId = 'someNodeId';
    const expectedResponse = { someKey: 'someValue' };
    mockModel.getValue.mockResolvedValue(expectedResponse);

    const result = await dataFetcher.fetchPageJson(nodeId);

    expect(result).toEqual(expectedResponse);
    expect(mockModel.getValue).toHaveBeenCalledWith(
      `mcm.versionedison.vl.versionedJsonIds["${nodeId}"].json`
    );
  });

  it('should throw an error when API call fails', async function() {
    const nodeId = 'invalidNodeId';
    const expectedError = new Error('Failed to get page JSON. Error from Falcor:');
    mockModel.getValue.mockRejectedValue(expectedError);

    await expect(dataFetcher.fetchPageJson(nodeId)).rejects.toThrow(expectedError);
    expect(mockModel.getValue).toHaveBeenCalledWith(
      `mcm.versionedison.vl.versionedJsonIds["${nodeId}"].json`
    );
  });
});p
